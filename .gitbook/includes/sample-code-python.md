---
title: sample-code-python
---

Requires Python 3.9 minimum and the [requests](https://pypi.org/project/requests/) library.

{% code lineNumbers="true" %}
```python
import json
import time
import requests
from pathlib import Path


def send_file_with_polling(
        file_path: str,
        model_id: str,
        api_key: str,
        max_retries: int = 30,
        polling_interval: int = 2,
) -> dict:
    file = Path(file_path)
    headers = {"Authorization": api_key}
    form_data = {"model_id": model_id, "rag": False}
    with open(file_path, "rb") as fh:
        files = {"file": (file.name, fh)}
        print(f"Enqueuing file: {file_path}")
        response = requests.post(
            url="https://api-v2.mindee.net/v2/inferences/enqueue",
            files=files,
            data=form_data,
            headers=headers,
        )
    response.raise_for_status()
    job_data = response.json().get("job")
    polling_url = job_data.get("polling_url")

    # Important to wait before attempting to poll
    time.sleep(3)

    # Poll for completion
    for attempt in range(max_retries):
        print(f"Polling on: {polling_url}")
        poll_response = requests.get(polling_url, headers=headers, allow_redirects=False)
        poll_data = poll_response.json()
        job_status = poll_data.get("job", {}).get("status")
        if poll_response.status_code == 302 or job_status == "Processed":
            result_url = poll_data.get("job", {}).get("result_url")
            print(f"Get result from: {result_url}")
            result_response = requests.get(result_url, headers=headers)
            result_data = result_response.json()
            return result_data
        # still processing, wait before next poll
        time.sleep(polling_interval)
    # If we've exhausted all retries
    raise TimeoutError(f"Polling timed out after {max_retries} attempts")


result = send_file_with_polling(
    file_path="/path/to/file.pdf",
    model_id="MY_MODEL_ID",
    api_key="MY_API_KEY",
)
print(json.dumps(result,indent=2))

```
{% endcode %}

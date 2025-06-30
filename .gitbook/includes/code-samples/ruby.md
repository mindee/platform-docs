---
title: sample-code-ruby
---

Requires Ruby 3.0 minimum. Could be greatly simplified if using RoR.

{% code lineNumbers="true" %}
```ruby
require 'uri'
require 'net/http'
require 'json'
require 'securerandom'

def send_file_with_polling(file_path, model_id, api_key, max_retries = 30, polling_interval = 2)
  # Upload file
  uri = URI.parse("https://api-v2.mindee.net/v2/inferences/enqueue")
  boundary = "----RubyFormBoundary#{SecureRandom.hex(8)}"
  file_name = File.basename(file_path)

  # Build multipart form data
  post_body = []
  post_body << "--#{boundary}\r\nContent-Disposition: form-data; name=\"model_id\"\r\n\r\n#{model_id}\r\n"
  post_body << "--#{boundary}\r\nContent-Disposition: form-data; name=\"rag\"\r\n\r\nfalse\r\n"
  post_body << "--#{boundary}\r\nContent-Disposition: form-data; name=\"file\"; filename=\"#{file_name}\""
  post_body << "\r\n#{File.binread(file_path)}\r\n--#{boundary}--\r\n"

  # Send initial request
  http = Net::HTTP.new(uri.host, uri.port)
  http.use_ssl = true
  request = Net::HTTP::Post.new(uri.request_uri)
  request["Authorization"] = api_key
  request["Content-Type"] = "multipart/form-data; boundary=#{boundary}"
  request.body = post_body.join

  response = http.request(request)
  if response.code.to_i >= 400
    raise "HTTP Error: #{response.code} - #{response.message}. Response body: #{response.body}"
  end
  polling_url = JSON.parse(response.body).dig("job", "polling_url")

  sleep(3)

  # Poll for results
  max_retries.times do
    puts "Polling on: #{polling_url}"
    uri = URI.parse(polling_url)
    poll_request = Net::HTTP::Get.new(uri)
    poll_request["Authorization"] = api_key
    http = Net::HTTP.new(uri.host, uri.port)
    http.use_ssl = true
    poll_response = http.request(poll_request)

    # Handle redirection or processed status
    if poll_response.is_a?(Net::HTTPRedirection) || poll_response.code == "302"
      result_url = poll_response["location"]
    else
      poll_data = JSON.parse(poll_response.body)
      if poll_data.dig("job", "status") == "Processed"
        result_url = poll_data.dig("job", "result_url")
      else
        sleep(polling_interval)
        next
      end
    end

    # Fetch results
    puts "Get result from: #{result_url}"
    uri = URI.parse(result_url)
    result_request = Net::HTTP::Get.new(uri)
    result_request["Authorization"] = api_key
    http = Net::HTTP.new(uri.host, uri.port)
    http.use_ssl = true
    return JSON.parse(http.request(result_request).body)
  end

  raise "Polling timed out after #{max_retries} attempts"
end

response = send_file_with_polling(
  "/path/to/file.pdf",
  "MY_MODEL_ID",
  "MY_API_KEY"
)
puts result
```
{% endcode %}

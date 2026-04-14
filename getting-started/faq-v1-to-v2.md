---
icon: comments-question-check
---

# Frequently Asked Questions

## 🚀 Why Mindee?

At Mindee, we've been listening to our customers and the evolving needs of document automation. Over the past years, we've learned that businesses don't just want to extract data from documents—they want to **understand, query, and act** on that data with complete autonomy.

* **From extraction to deeper intelligence**: Enhancing our proven AI capabilities with advanced features like RAG, enabling you to not just extract data but have conversations with your documents
* **From developer-focused to universally accessible**: Building on V1's solid API foundation while adding intuitive self-service tools that empower both technical and non-technical users
* **From powerful APIs to comprehensive platform**: Expanding beyond our robust V1 APIs to offer a complete ecosystem where users can build, test, and deploy document automation solutions with greater flexibility
* **User empowerment**: Proactive tools and insights that help users solve challenges independently when they prefer

## **Technical Changes**

### **API & Integration**

<details>

<summary>How will API calls change in V2?</summary>

Models are fully customizable and unique. As such, there is a single API route to send documents for processing. This single route requires the model ID to be given, along with other optional parameters.

The resulting output has a different output structure which is much more generic to allow for the unique and custom nature of the models.

[api-overview.md](../integrations/api-overview.md "mention")

</details>

<details>

<summary>Can I use the same V1 API keys in the V2?</summary>

No, V1 and V2 do not share API key information.

</details>

<details>

<summary>Are there webhook capabilities?</summary>

Yes, the API supports webhook integration for asynchronous document processing.

[webhooks.md](../integrations/webhooks.md "mention")

</details>

<details>

<summary>How do rate limits work?</summary>

Check the [#rate-limits](../integrations/technical-limitations.md#rate-limits "mention") section.

</details>

### Models performance

<details>

<summary>What new document types are supported?</summary>

You can create a custom extraction model for any document type.

</details>

<details>

<summary>Which countries/languages are supported?</summary>

V2 models are optimized for global use, we support [most languages and alphabets](https://docs.mindee.com/models/data-schema#extraction-guidelines), and thus documents from most countries.

</details>

<details>

<summary>Can I create custom extraction templates?</summary>

Yes, V2 allows full control for the users with interactive model customization.

</details>

<details>

<summary>What file formats are supported?</summary>

Supported formats include PDF, PNG, JPEG, and TIFF, similar to V1. Multi-page PDFs and high-res images are fully compatible.

[#accepted-files](../integrations/technical-limitations.md#accepted-files "mention")

</details>

<details>

<summary>How do I optimize performances for my specific use case?</summary>

In order to optimize the performance of a given model, the first step is to follow the [data-schema-best-practices.md](../extraction-models/data-schema-best-practices.md "mention") so that the model performances are globally better.

If after this step, some unexpected behavior happen on some isolated templates, [improving-accuracy.md](../extraction-models/optional-features/improving-accuracy.md "mention") can to be used to increase performances on these given templates, with no regression on the rest of the flow.

</details>

### Development & Testing

<details>

<summary>Which programming languages are supported?</summary>

We officially support Python, Node.js, Ruby, PHP, Java and .NET, when these are used in conjunction with our official client libraries.

[client-libraries-sdk](../integrations/client-libraries-sdk/ "mention")

For no-code/low-code, we officially support Make.com, n8n, and Zapier

[no-code-integrations](../integrations/no-code-integrations/ "mention")

However, any language or system able to make an HTTP call and receive a JSON response can be used and supported by the community.

</details>

<details>

<summary>Is there a sandbox environment for testing?</summary>

No. We only have one environment available, which is the one you can use for your tests.

</details>

<details>

<summary>How do I migrate my existing code to V2?</summary>

You’ll need to create a new code integration. Use one of our official client libraries to speed up this process.

</details>

## Feature Comparison & Use Cases

### Feature Analysis

<details>

<summary>What advanced features should I consider adopting?</summary>

V2's most impactful advanced features include:

**AI-Powered Model Customization:**

* **Model creation and Data Schema modification using our AI assistant**: Easily create custom extraction models tailored to your specific document types without technical expertise
* **Interactive model set up**: Easily change the data schema to modify your model behavior in seconds by adding, modifying, removing fields and add specific guidelines.

**RAG (Retrieval Augmented Generation):**

* **Document database enhancement**: Add your processed documents to the RAG database to improve extraction accuracy over time
* **AI learning from corrections**: Teach the AI correct answers when it makes mistakes, continuously improving performance for your specific use cases
* **Contextual understanding**: Enable the AI to understand document context and relationships for more accurate data extraction

**Combined Benefits:** These features work together to create a self-improving system that becomes more accurate and efficient as you use it, reducing manual corrections and improving automation success rates.

</details>

<details>

<summary>Do you still have a roadmap for APIs of the old platform?</summary>

No — V1 APIs are no longer being developed. The focus has fully shifted to V2, which supports more advanced use cases and enables faster iteration. Free plan users will be deprecated on September 15, 2025. We strongly recommend migrating now to benefit from the improved capabilities and avoid service disruption.

</details>

## Commercial & Pricing Changes

### Pricing Structure & Strategy

For more information, see the [billing](https://docs.mindee.com/account-management/billing) and [plans](https://docs.mindee.com/account-management/plans) documentation.

<details>

<summary>Are there volume discounts for enterprise customers?</summary>

We offer volume discounts for customers who process over 250,000 pages per year. To discuss tailored pricing options that suit your volume requirements, please reach out to our Sales Team directly from your billing page. Our volume pricing packages feature competitive rates per page, custom Service Level Agreements (SLAs), and flexible terms.

</details>

<details>

<summary>How do overage charges work if I exceed my plan limits?</summary>

When you exceed your plan limits, overage charges are automatically billed on your credit card either when you reach €100 in overages or at the end of your subscription billing cycle, whichever comes first.

</details>

<details>

<summary>Can I try before committing to a paid plan?</summary>

We offer a 14-day & 500-page free trial (no credit card required), allowing you to test all features and functionality (Continuous Learning, API Keys, Polygons,…) before committing to a paid plan.

</details>

### Billing Operations

<details>

<summary>How does billing work?</summary>

Payment is required upfront to access the platform and the features included in your plan. Only extra calls (if you have exceed the ones included in your plan) will be invoiced every 100€ or at the end of your subscription.

</details>

<details>

<summary>When does billing start?</summary>

You will be billed as soon as you complete your subscription payment online.

</details>

<details>

<summary>What payment methods are accepted?</summary>

At this time, V2 subscriptions can only be purchased using credit cards (expect for Enterprise Plan

</details>

<details>

<summary>How do I handle tax and invoicing requirements?</summary>

You can see all the details about your pending subscription by clicking on “Manage Plan” under the billing section.

</details>

## Legal & Security

### Data Protection & Privacy

<details>

<summary>What changes to data processing and localization?</summary>

You can now set yourself the data processing rules directly in the Settings Page of each model. To see more details about those parameters, you can check the [Model Settings page](https://docs.mindee.com/models/model-settings#processing-zone).

</details>

<details>

<summary>How does data residency work?</summary>

Mindee V2 allows you to choose your data residency region (EU or US) at the model or organizational level, with the [#processing-zone](../models/model-settings.md#processing-zone "mention"). All document processing and storage then take place exclusively in that region, ensuring compliance with local regulations.

</details>

<details>

<summary>What regions are available for data processing?</summary>

Currently, you can choose between Europe (EU) and United States (US) for your data processing region.

</details>

<details>

<summary>How is my data protected during RAG processing?</summary>

In RAG (Retrieval-Augmented Generation), your data remains private and isolated within your model. All documents added to your RAG database are encrypted in transit and at rest. No data is shared across customers, and the AI does not train on your data globally — only your private models benefit from your inputs.

</details>

<details>

<summary>Are there changes to data retention policies?</summary>

Yes. In V2, you have more control over retention. You can set everything up using the [Model Settings page](https://docs.mindee.com/models/model-settings#processing-zone).

</details>

<details>

<summary>Is Mindee GDPR &#x26; SOC 2 Type II compliant?</summary>

Yes. Mindee V2 is fully GDPR-compliant and maintains its SOC 2 Type II certification, ensuring rigorous security controls, data protection standards, and transparency for enterprise needs.

</details>

<details>

<summary>What happens to my data if I cancel my subscription?</summary>

If you cancel your subscription, your data will be retained for 30 days to allow for potential reactivation or export. After this grace period, your documents and models will be automatically deleted, in accordance with our data lifecycle policy.

</details>

<details>

<summary>Can I request data deletion at any time?</summary>

Yes. You can request full or partial data deletion at any time by contacting support, or by using the deletion features available in your model settings, depending on your plan. Mindee ensures that your data is securely and permanently removed upon request.

</details>

## Migration & support

### Migration & support

<details>

<summary>Can I run V1 and V2 in parallel?</summary>

Yes, absolutely. Running both platforms in parallel is not only supported but recommended for a smooth transition

</details>

<details>

<summary>What's the step-by-step migration process?</summary>

**Quick Overview:**

1. **Assessment**: Analyze your current V1 usage and identify V2 plan requirements
2. **Setup**: Create your V2 account and configure basic settings
3. **Testing**: Use our migration testing checklist (see below)
4. **Integration**: Update your applications with V2 API endpoints
5. **Validation**: Run parallel processing to compare results
6. **Cutover**: Gradually shift traffic from V1 to V2
7. **Optimization**: Leverage V2's new features to enhance your workflows

**Documentation Includes:**

* Code examples for common migration scenarios
* Troubleshooting guides for common migration issues
* Rollback procedures if needed

</details>

<details>

<summary>What migration support is provided?</summary>

Mindee V2 offers 1:1 support for Business and Enterprise customers, with step-by-step upgrade paths to help you transition from V1 to V2 smoothly.

</details>

<details>

<summary>What happens if I encounter issues during migration?</summary>

If you face issues, you can contact Mindee’s support team via Intercom or email. For Business and Enterprise plans, priority assistance is available to resolve migration blockers quickly.

</details>

### Data & Configuration Migration

<details>

<summary>Can I migrate my existing documents and processing configurations?</summary>

No, you’ll need to manually re-upload the documents to your RAG for instance. For Enterprise users, we can offer this transition as a service.

</details>

<details>

<summary>What about existing webhooks and callbacks?</summary>

You’ll need to reconfigure webhooks in V2 as the endpoint structure and authentication method differ from V1.

</details>

## Resources

### Learning & Documentation

<details>

<summary>How do I stay updated on new features?</summary>

You can give feedback and follow product updates directly in [https://feedback.mindee.com/](https://feedback.mindee.com/)

</details>

<details>

<summary>How can I ask for a feature or give a feedback?</summary>

You can give feedback and follow product updates directly in [https://feedback.mindee.com/](https://feedback.mindee.com/)

</details>

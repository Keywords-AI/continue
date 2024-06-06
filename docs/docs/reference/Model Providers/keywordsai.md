# Keywords AI

[Keywords AI](https://keywordsai.co) is a unified developer platform where you can call 150+ LLM using the OpenAI format with one API key and get insights into your AI products. With 2 lines of code, you can build better AI products with complete observability. The full list of supported models by Keywords AI can be found in the [page](https://platform.keywordsai.co/platform/models).

Change `~/.continue/config.json` to look like the following. Since Keywords AI is fully API compatible with OpenAI, it is recommended to stick with `"provider": "openai"`, even if they aren't necessarily the upstream provider.

```json title="~/.continue/config.json"
{
  "models": [
    {
      "title": "Keywords AI GPT 4o",
      "provider": "openai",
      "model": "gpt-4o",
      "apiBase": "https://api.keywordsai.co/api/",
      "apiKey": "Your_Keywords_AI_API_Key"
    }
  ]
}
```

To utilize features such as provider preferences or model routing configuration, include these parameters inside the `models[].requestsOptions.extraBodyProperties` field of your plugin config.

Suppose you want your AI products to be more robust and have better observability, such as having fallback models when primary models fail or knowing more about user activities. In that case, you can add parameters like fallback_models and customer_identifier in the extra_body param from OpenAI:

```json title="~/.continue/config.json"
{
  "models": [
    {
      ...
      "requestOptions": {
        "extraBodyProperties": {
          "fallback_models": ["gpt-4-turbo"],
          "customer_identifier": "your_customer_identifier"
        }
      }
    }
  ]
}
```

Learn more about available settings [here](https://docs.keywordsai.co/get-started/overview).

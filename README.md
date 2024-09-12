# Go-ChatGPT

Go-ChatGPT is an open-source GoLang client for ChatGPT, a large language model trained by OpenAI. With Go-ChatGPT, you can integrate ChatGPT's language processing capabilities into your Go applications.

## Features

- Provides a GoLang client for ChatGPT.
- Sends text to ChatGPT and receives a response from ChatGPT.
- Supports GPT4, GPT4o, GPT3.5, and o1 models.

## Installation

You can install Go-ChatGPT by using Go modules:

```bash
go get github.com/josh-wong/go-chatgpt
```

## Getting started

Get your [API key from the OpenAI Dashboard](https://platform.openai.com/account/api-keys) and export this either as an environment variable or put the API key in your `.bashrc` or `.zshrc` file, replacing `<YOUR_OPENAI_API_KEY>` with your API key:

```console
export OPENAI_KEY=<YOUR_OPENAI_API_KEY>
```

___

1. In your Go code, import the Go-ChatGPT package.

  ```go
  import (
    "github.com/josh-wong/go-chatgpt"
  )
  ```

2. Create a new ChatGPT client that uses your API key.

  ```go
    key := os.Getenv("OPENAI_KEY")

    client, err := chatgpt.NewClient(key)
  if err != nil {
    log.Fatal(err)
  }
  ```

3. Use the `SimpleSend` API to send text to ChatGPT and get a response.

  ```go
  ctx := context.Background()

  res, err := c.SimpleSend(ctx, "Hello, how are you?")
  if err != nil {
  // Handle errors.
  }
  ```

  The SimpleSend method will send the specified text to ChatGPT and return a response. If an error occurs, an error message will be returned.

4. To use a model and/or parameters, use the `Send` API. For example, the following uses the gpt-4o-mini (`GPT4oMini`) model.

  ```go
  ctx := context.Background()

  res, err = c.Send(ctx, &chatgpt.ChatCompletionRequest{
    Model: chatgpt.GPT4oMini,
    Messages: []chatgpt.ChatMessage{
      {
        Role: chatgpt.ChatGPTModelRoleSystem,
        Content: "Hey, explain GoLang to me in two sentences.",
      },
    },
  })
  if err != nil {
  // Handle errors.
  }
  ```

## Contribute

If you want to contribute to this project, feel free to open a PR or an issue.

## License

This package is licensed under the MIT license. See [LICENSE](./LICENSE) for details.

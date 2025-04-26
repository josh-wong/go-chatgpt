# Go-ChatGPT

Go-ChatGPT is an open-source GoLang client for OpenAI's large language models (LLMs). By using this client, you can integrate the language-processing capabilities of OpenAI's LLMs into your Go-based applications.

## Features

- Provides a GoLang client for OpenAI's LLMs.
- Supports a variety of [OpenAI models](#list-of-supported-models).
- Sends text to OpenAI and receives a response from the LLM that you chose.

### List of supported models

<details>
<summary>💭Reasoning models</summary>

| **Model name**                        | **Alias**                                      |
| ---------------------------------- | ----------------------------------- |
| **o4Mini✨**                            | `o4-mini`                                      |
| **o3✨**                                   | `o3`                                              |
| **o3Mini**                                 | `o3-mini`                                      |
| **o1**                                        | `o1`                                              |
| **o1Mini**                                 | `o1-mini`                                      |
| **o1Pro✨**                              | `o1-pro`                                       |
</details>

<details>
<summary>💬Flagship chat models</summary>

| **Model name**                          | **Alias**                                      |
| ----------------------------------- | ----------------------------------- |
| **GPT4_1✨**                             | `gpt-4.1`                                      |
| **GPT4o**                                   | `gpt-4o`                                       |
| **GPT4oAudioPreview✨**        | `gpt-4o-audio-preview`             |
| **ChatGPT4o✨**                       | `chatgpt-4o-latest`                    |
</details>

<details>
<summary>💵Cost-optimized models</summary>

| **Model name**                          | **Alias**                                      |
| ----------------------------------- | ----------------------------------- |
| **GPT4_1Mini✨**                      | `gpt-4.1-mini`                             |
| **GPT4_1Nano✨**                    | `gpt-4.1-nano`                           |
| **GPT4oMini**                            | `gpt-4o-mini`                             |
| **GPT4_1Audio✨**                   | `gpt-4.1-audio-preview`             |
</details>
<details>
<summary>⌚Realtime models</summary>

| **Model name**                          | **Alias**                                      |
| ----------------------------------- | ----------------------------------- |
| **GPT4oRealtime✨**                | `gpt-4o-realtime-preview`          |
| **GPT4oMiniRealtime✨**         | `gpt-4o-mini-realtime-preview` |
</details>

<details>
<summary>🖼️Image generation models</summary>

| **Model name**                          | **Alias**                                      |
| ----------------------------------- | ----------------------------------- |
| **GPTImage1✨**                      | `gpt-image-1`                             |
| **DALLE3✨**                             | `dall-e-3`                                    |
</details>

<details>
<summary>🗣️Text-to-speech models</summary>

| **Model name**                          | **Alias**                                      |
| ----------------------------------- | ----------------------------------- |
| **GPT4oMiniTTS✨**                 | `gpt-4o-mini-tts`                         |
| **TTS1✨**                                 | `tts-1`                                          |
| **TTS1HD✨**                            | `tts-1-hd`                                    |
</details>

<details>
<summary>✍🏻Transcription models</summary>

| **Model name**                          | **Alias**                                      |
| ----------------------------------- | ----------------------------------- |
| **GPT4oTranscribe✨**              | `gpt-4o-transcribe`                     |
| **GPT4oMiniTranscribe✨**       | `gpt-4o-mini-transcribe`            |
| **Whisper✨**                            | `whisper-1`                                 |
</details>

<details>
<summary>🛠️Tool-specific models</summary>

| **Model name**                          | **Alias**                                      |
| ----------------------------------- | ----------------------------------- |
| **GPT4oSearchPreview✨**        | `gpt-4o-search-preview`            |
| **GPT4oMiniSearchPreview✨** | `gpt-4o-mini-search-preview`   |
| **ComputerUsePreview✨**       | `computer-use-preview`            |
</details>

## Installation

You can install or upgrade Go-ChatGPT by using Go modules, run the following command, replacing `<MAJOR.MINOR.PATCH>` with the version that you want to install:

```bash
go install github.com/josh-wong/go-chatgpt@v<MAJOR.MINOR.PATCH>
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

3. Use the `SimpleSend` API to send text to OpenAI and get a response.

  ```go
  ctx := context.Background()

  res, err := c.SimpleSend(ctx, "Hello, how are you?")
  if err != nil {
  // Handle errors.
  }
  ```

  The SimpleSend method will send the specified text to OpenAI and return a response. If an error occurs, an error message will be returned.

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

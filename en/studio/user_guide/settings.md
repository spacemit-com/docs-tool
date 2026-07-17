---
sidebar_position: 9
---

# Settings

Click the ⚙️ icon to open the Settings page, where the appearance, cache, AI models, and remote gateway for SpacemiT Studio can be configured.

![Settings page](../static/setting_00.png)

## Appearance

- **Theme Mode**: Switches between light and dark themes.
- **Language**: Switches the interface language (Chinese/English).

## Cache Management

- **Cache Directory**: Click **Change** to modify the default download and storage path. A non-system drive is recommended.
- **Image Directory**: Click **Clear** to delete downloaded raw image files. Deleted image files must be downloaded again before use.
- **Extraction Directory**: Click **Clear** to delete extracted files. Before clearing, verify that no active projects still depend on this directory.

## AI Settings

- **Add Model**: Click **+ Add Model**, fill in the following information, then click **OK**:
  ![Add model dialog](../static/setting_02.png)
  - **Name**: A custom display name for the model.
  - **Provider**: The model service provider (such as OpenAI or ByteDance).
  - **API Key**: The key used for authentication.
  - **Model ID**: The identifier used to invoke the model (such as `gpt-4o` or `doubao-seed-1-6`).
  - **Max Tokens**: The maximum number of tokens allowed per request. Leave blank to use the provider's default value.

## Remote Gateway

- **Disabled (default)**: Connects directly to the local driver. Suitable for local development and debugging.
- **Enabled**: When enabled, fill in the following information and click **Test & Save**:
  - **Gateway Address**: The address of the remote gateway.
  ![Remote gateway settings](../static/setting_01.png)

## About

Displays the current SpacemiT Studio version.

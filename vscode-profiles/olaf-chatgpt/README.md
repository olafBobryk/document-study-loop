# Olaf's ChatGPT VS Code Profile

This is Olaf's personal lightweight `ChatGPT` VS Code profile for Document Study Loop-style Markdown study work.

It mirrors the local VS Code `ChatGPT` profile and includes:

- Markdown preview and editing extensions
- PDF and Office document viewers
- Markdown keybindings for editor and preview workflows
- the profile's current viewer settings

Import `olaf-chatgpt-vscode.code-profile` from VS Code with:

1. Open VS Code.
2. Run `Profiles: Import Profile...`.
3. Choose this local `.code-profile` file.

Extension fallback:

```sh
code --profile "ChatGPT" --install-extension shd101wyy.markdown-preview-enhanced
code --profile "ChatGPT" --install-extension yzhang.markdown-all-in-one
code --profile "ChatGPT" --install-extension zaaack.markdown-editor
code --profile "ChatGPT" --install-extension tomoki1207.pdf
code --profile "ChatGPT" --install-extension cweijan.vscode-office
```

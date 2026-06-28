# ChatGPT Study Loop VS Code Profile

This is a lightweight, shareable VS Code profile seed for Document Study Loop users.

It is based on the local `ChatGPT` profile used for Markdown study runs and includes only:

- Markdown preview and editing extensions
- PDF and Office document viewers
- two Markdown keybindings
- generic viewer settings

Import `chatgpt-study.code-profile` from VS Code with:

1. Open VS Code.
2. Run `Profiles: Import Profile...`.
3. Choose this local `.code-profile` file.

Recommended fallback:

```sh
code --profile "ChatGPT" --install-extension shd101wyy.markdown-preview-enhanced
code --profile "ChatGPT" --install-extension yzhang.markdown-all-in-one
code --profile "ChatGPT" --install-extension zaaack.markdown-editor
code --profile "ChatGPT" --install-extension tomoki1207.pdf
code --profile "ChatGPT" --install-extension cweijan.vscode-office
```

To publish a VS Code-hosted profile link, open the `ChatGPT` profile and run `Profiles: Export Profile...`, then choose the GitHub/Gist sharing option.

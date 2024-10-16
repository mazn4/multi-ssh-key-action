# Multi SSH Key Action

This GitHub Action sets up multiple SSH keys for accessing private GitHub repositories.

## Inputs

### `ssh_keys`

**Required** A multi-line input of SSH keys. Each line should be in the format: `KEY_NAME=SSH_KEY_CONTENT`

## Example usage

```yaml
uses: mazn4/multi-ssh-key-action@v1
with:
  ssh_keys: |
    repo1=${{ secrets.REPO1_PRIVATE_KEY }}
    id_rsa_repo2=${{ secrets.REPO2_PRIVATE_KEY }}
    id_ed25519_repo3=${{ secrets.REPO3_PRIVATE_KEY }}
```

## How it works

1. The action securely adds GitHub's public keys to known hosts.
2. It sets up an SSH config file for valid keys.
3. It starts an SSH agent and adds all valid private keys to it.
4. The SSH_AUTH_SOCK environment variable is set for subsequent steps in your workflow.

## Note

Ensure that your secrets are properly set in your repository settings. Never expose your private keys in your workflow files.

This action is specifically designed for use with GitHub repositories.

## Troubleshooting

If you encounter any issues while using this action, please check the following:

1. Ensure your SSH keys are correctly formatted and valid.
2. Check that your secrets are properly set in your repository settings.
3. Verify that you have the necessary permissions to access the target repositories.

If problems persist, please open an issue in the GitHub repository for this action.

## Contributing

Contributions to improve Multi SSH Key Action are welcome! Please feel free to submit pull requests or open issues to suggest improvements or report bugs.

## License

This project is licensed under the MIT License - see the LICENSE file for details.
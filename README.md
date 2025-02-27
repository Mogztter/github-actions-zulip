# Zulip Send Message Action

[![GitHub Action badge](https://github.com/zulip/github-actions-zulip/workflows/test-local/badge.svg)](https://github.com/zulip/github-actions-zulip/actions?query=workflow%3Atest-local)

This action sends a message to [Zulip](https://zulip.com/).

## Inputs

### `api-key`

**Required** [API key](https://zulip.com/api/api-keys) used to interact with the Zulip API. You can get an API key through Zulip's web interface.

### `email`

**Required** Email address of the user who owns the API key mentioned above.

### `organization-url`

**Required** Zulip organization canonical URL.

### `to`

**Required** For stream messages, either the name or integer ID of the stream.
For private messages, either a list containing integer user IDs or a list containing string email addresses.

### `type`

**Required** The type of message to be sent. `private` for a private message and `stream` for a stream message.
Must be one of: `private`, `stream`.

### `topic`

**Optional** The topic of the message. Only required for stream messages (`type="stream"`), ignored otherwise.
Maximum length of 60 characters.

### `content`

**Required** The content of the message. Maximum message size of 10000 bytes.
Format your message using [Zulip Markdown](https://zulip.com/help/format-your-message-using-markdown).

## Example usage

**Send a stream message**
```yml
- name: Send a stream message
  uses: zulip/github-actions-zulip@v0.2.0
  with:
    api-key: 'abcd1234'
    email: 'username@example.com'
    organization-url: 'https://org.zulipchat.com'
    to: 'social'
    type: 'stream'
    topic: 'Castle'
    content: 'I come not, friends, to steal away your hearts.'
```

**Send a private message**
```yml
- name: Send a private message
  uses: zulip/github-actions-zulip@v0.2.0
  with:
    api-key: 'abcd1234'
    email: 'username@example.com'
    organization-url: 'https://org.zulipchat.com'
    to: '9' # user_id
    type: 'private'
    content: 'With mirth and laughter let old wrinkles come.'
```

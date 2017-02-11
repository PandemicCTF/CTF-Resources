# Code snippets

Some useful commands or small snippets.

## `openssl`

Decrypt message with RSA private key:

```
openssl rsautl -decrypt -inkey private.key -in message.bin
```

It'll ask for a pass phrase, if there is any.
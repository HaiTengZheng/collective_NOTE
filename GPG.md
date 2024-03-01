# gpg
## gen-key
> gpg --full-gen-key
## list
> gpg --list-keys

# file location
> $HOME/.gnupg

# --armor
used to export the keys in Privacy Enhanced Mail(PEM) format
> gpg --armor --export-secret-keys foobar@example.com > privacy.pem

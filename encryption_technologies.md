# GPG
> .gnupg/
## install `pinentry` package
> sudo dnf install pinentry
## create pair of GPG
> gpg --full-generate-key
## list keys
> gpg --list-keys
## symmetrically enctypting your own files
> gpg -c secret_squirrel_stuff.txt
the `-c` option indicates that i chose to use symmetric encryption with a passphrase
for the file, the passphrase that you enter will be for the file, not for your 
private key

- One slight flaw with this is that GPG makes an enctypted copy of the file,
  but it also leaves the original unencrypted file intact
# decrypt
- `-o` the decrypted file that we want to create
- `-d` decrypt
> gpg -o secret_squirrel_stuff.txt -d secret_squirrel_stuff.txt.gpg

================================================================================
# shred
git rid of that unencrypted file
- the `-u` option to delete the file
- the `-z` option to overwrite the deleted file with zeros

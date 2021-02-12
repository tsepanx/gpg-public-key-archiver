# gpg-public-key-archiver

A small encryption project, to simplify managing files encryption with `gpg`.

It's purpose is to encrypt data by your public gpg key, 
and then archiving it to one file, without the need to decrypt it firstly with secret key.

### Encrypting

Supposing you have some data in `folder/` directory, 
and you public key with `mykey@abc.net` idenity,
You can simply do

```
zip -r folder.zip folder/
gpg -r mykey@abc.net --encrypt folder.zip
```
to get 1 encrypted file `folder.zip.gpg`

But afterwards, there is no ability for you to decrypt it again, to add some extra file, for example.

So, assuming you have no access to your secret gpg key, this script creates a new folder, with previous `folder.zip.gpg` file, and your extra `new_folder/` that you want to add.
```
result_folder/
   ├── folder.zip.gpg
   └── new_folder/
```
Gets to `result_folder.zip.gpg`

### Decrypting
When you get your secret key in gpg keyring, it's time to get all files back.

Decrypting file goes the same, but in reverse order
```
gpg --decrypt result_folder.zip.gpg > result_folder.zip
unzip result_folder.zip
```
Finally, you get `result_folder/`

### Motivation
So, that script automates such encrypting & decrypting commands

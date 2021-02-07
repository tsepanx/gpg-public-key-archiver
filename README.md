# gpg-public-key-archiver

This project purpose is to encrypt data by your public gpg key, 
and then archiving it to one file, without the need to decrypt it firstly with secret key.

Supposing you have some data in `folder/` directory, 
and you public key with `mykey@abc.net` idenity,
You can simply do

```
zip -r folder.zip folder/
gpg -r mykey@abc.net --encrypt folder.zip
```
to get 1 encrypted file `folder.zip.gpg`

But afterwards, there is no ability for you to decrypt it again, to add some extra file, for example.

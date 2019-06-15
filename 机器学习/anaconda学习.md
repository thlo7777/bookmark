### [NotWritableError: The current user does not have write permissions to a required path.](https://github.com/conda/conda/issues/7267)
```text
 I discovered that when I installed anaconda, I did so with sudo so the owner of the folder was root. 
 This worked for me to fix this.

 sudo chown -R username /path/to/anaconda3

 obviously replace "username" with your username and the correct path to anaconda3
```
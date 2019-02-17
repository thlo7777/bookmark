# install issue

## 1. ```curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - ```

>**return gpg: no valid OpenPGP data found**
>You can manually download that file ```https://packages.cloud.google.com/apt/doc/apt-key.gpg``` and then do `cat apt-get.pgp | apt-key add -`
<https://github.com/dart-lang/sdk/issues/34967>
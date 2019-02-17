# install issue

**1.** **```curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - ```**
>return gpg: no valid OpenPGP data found
This has to do with `curl`. You can manually download that file `https://dl-ssl.google.com/linux/linux_signing_key.pub` and then do `cat linux_singing_key.pub | apt-key add -`
<https://github.com/dart-lang/sdk/issues/34967>
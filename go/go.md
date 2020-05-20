## Go lang 笔记

#### [golang的win10安装](https://www.jianshu.com/p/164d50dd7c8f)

#### [vs code command 'go.tools.install' not found](https://stackoverflow.com/questions/59806254/command-go-tools-install-not-found)

#### [vs code go Autoimport not working](https://github.com/microsoft/vscode-go/issues/2473)
```
You need to make sure to use this configuration(from https://github.com/golang/go/wiki/gopls#editors-instructions) to get the auto-import feature back:

"go.testEnvFile": "",
"go.useLanguageServer": true,
"go.languageServerExperimentalFeatures": {
        "diagnostics": true // for diagnostics as you type
},
"[go]": {
    "editor.snippetSuggestions": "none",
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
        "source.organizeImports": true
    },
},
"gopls": {
    "usePlaceholders": true,
    "completeUnimported": true
},  
```
#### [golang之package](https://www.ctolib.com/topics-4852.html())

#### [关于go中的package和main关系](https://blog.csdn.net/xinbaobaoer/article/details/76991182)

#### [如何在Go中编写包](https://www.howtoing.com/how-to-write-packages-in-go)
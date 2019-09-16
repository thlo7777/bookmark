### [NotWritableError: The current user does not have write permissions to a required path.](https://github.com/conda/conda/issues/7267)
```text
 I discovered that when I installed anaconda, I did so with sudo so the owner of the folder was root. 
 This worked for me to fix this.

 sudo chown -R username /path/to/anaconda3

 obviously replace "username" with your username and the correct path to anaconda3
```

### [install open cv in conda]
```text
To install this package with conda run one of the following:
conda install -c conda-forge opencv 
conda install -c conda-forge/label/gcc7 opencv 
conda install -c conda-forge/label/broken opencv 
conda install -c conda-forge/label/cf201901 opencv 
```

### [Install tensorflow in anconda](https://www.anaconda.com/tensorflow-in-anaconda/)
```text
TensorFlow and activate it

    $>conda create -n tensorflow_env tensorflow
 	$>conda activate tensorflow_env
 	
-----------------
Or for the GPU version

    $>conda create -n tensorflow_gpuenv tensorflow-gpu
    $>conda activate tensorflow_gpuenv
```

### [Exit from conda virtual environment]
```text
 conda deactivate
```

### [Windows10下安装Anaconda3(64位)详细过程](https://blog.csdn.net/ychgyyn/article/details/82119201)
```
进入Anaconda的官网进行下载或学习。
选择你想下载的Python版本，这里我们选择的是Python3.6
选择你的操作系统和位数，这里我们选择的是Windows64位
然后点击Download按钮就开始下载了
```

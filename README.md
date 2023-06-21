磨刀不误砍材工，在搭建之前先去看看自己的磁盘空间够不够一个完整的stable diffusion 大概需要20~30个g如何查找自己磁盘空间这个东西应该不需要在这里赘述。当做好这个准备工作之后我们就可以开始搭建了。

# 1.部署必须项以及要点

## 1.1 所需软件

Git的安装与注意事项

搜索https://git-scm.com/download/win，找到download，根据自己的系统选择合适的git版本。在本次搭建中对于git版本没有限制，它只是一个后面克隆的工具。

 

![image](https://github.com/jl696/miniature-fishstick/assets/136220665/efcd7e18-24c1-4948-84d9-52228a2ddfc4)


 


​                                

 

Python的安装与注意事项

搜索https://www.python.org/downloads/windows/找到一个适合自己的版本即可。（注意版本应该在3.10版本及以上这是stable diffusion官方文档中要求的我使用的是3.10.3）

 

Nvidia CUDA

使用CUDA技术可以高效地利用GPU的并行计算能力和通用计算能力，简而言之CUDA对于提高你电脑gpu的运算能力很有帮助。点击https://developer.download.nvidia.cn/compute/cuda 找到自己的驱动版本固定搭配的CUDA版本在Windows下，安装CUDA一般只用根据安装程序的提示就可以安装了。如果你不想安装太多冗余的东西，则可以只在安装选项中勾选Runtime和Development（如果你不知道如何操作，可以在安装完成后再在系统设置中卸载）

在开始之前检查磁盘的剩余空间（一个完整的Stable diffusion即加载了模型的大概要占用20~30的空间）。

​              

## 1.2开始克隆

打开Windows终端进入到你想克隆的位置进行克隆，接着使用git克隆AUTOMATIC1111的stable-diffusion-webui（这里我是用了Ghproxy在国内进行加速）加速确实会快一点：

git clone https://ghproxy.com/https://github.com/AUTOMATIC1111/stable-diffusion-webui.git

克隆完成后，进入到克隆好的目录。

cd .\stable-diffusion-webui。

1.1.1 venv虚拟环境的构建

   完成后你需要进入Stable Diffusion自带的Venv虚拟Python环境以进行配置和安装依赖。由于刚克隆下来的Stabe Diffusion没有附带Venv，所以我们得先执行一遍如下命令，以创建一个Venv环境。

 

python -m venv .\venv

 

创建完成以后，我们进入到venv目录中的Scripts文件夹：

 

cd .\venv\Scripts

 

进入之后最好更换pip源，以方便后续的各种PIP包的安装我选择的是豆瓣的镜像源源pip config set global.index-url http://pypi.douban.com/simple/

接着我们需要安装stable diffusion和WebUI所需的PIP包了。开始执行命令后一定要耐心等待安装完成要是就得慢也不要随意去动网络。首先退出到stable diffusion-webui中先执行安装依赖项的命令pip install -r requirements_versions.txt 然后再执行webui-user.bat最后便是漫长的等待。

运行完这一步stable diffusion的基本框架就已经被我们安装好了

# 2.常见问题以及解决方法

## 2.1  Couldn‘t install gfpgan

在运行webui-user.bat时如果网络不好就会导致的一个报错，就算你使用了加速器也有概率会出现这个问题终其原因都是网络不好连接不上。

解决方案：

1.打开cmd

2.进入你所克隆的盘里面

3.输入cd e:\aii\stable-diffusion-webui\venv\Scripts

4.输入 git clone https://github.com/TencentARC/GFPGAN.git (这上面的e:\aii\是我的目录根据自己的目录来具体编写代码)

6.安装完成后cd GFPGAN

7.输入e:\aii\stable-diffusion-webui\venv\Scripts\python.exe -m pip install

\8. 等待完成之后输入e:\aii\stable-diffusion-webui\venv\Scripts\python.exe -m pip install -r requirements.txt

\9. 等待下载完成之后输入e:\aii\stable-diffusion-webui\venv\Scripts\python.exe setup.py develop

10.等待下载完成之后输入e:\aii\stable-diffusion-webui\venv\Scripts\python.exe setup.py develop

11.等待下载完成之后输入e:\aii\stable-diffusion-webui\venv\Scripts\python.exe -m pip install realesrgan

12.完成之后运行webui-user.bat即可

当你再次运行webui-user.bat时会发现已经跳过了install gfpgan这一步。

## 2.2 其他常见错误

要是出现报错理由是什么Couldn‘t  什么的。例如Couldn‘t clone Taming Transformers之类的基本上还是网络的问题。

解决办法

删除已经存在的文件夹 例如Couldn‘t clone Taming Transformers就去把Taming Transformers这个文件夹给删掉。然后再开始接下来的操作

Couldn‘t clone Taming Transformers 

输入git clone https://github.com/CompVis/taming-transformers.git “e:\aii\stable-diffusion-webui\repositories\taming-transformers”

Couldn’t clone k_diffusio 

输入git clone https://github.com/crowsonkb/k-diffusion.git “e:\aii\stable-diffusion-webui\repositories\k-diffusion”

Couldn‘t clone CodeFormer 

输入git clone https://github.com/sczhou/CodeFormer.git “e:\aii\stable-diffusion-webui\repositories\CodeFormer”

Couldn’t clone BLIP

输入git clone https://github.com/salesforce/BLIP.git “e:\aii\stable-diffusion-webui\repositories\BLIP

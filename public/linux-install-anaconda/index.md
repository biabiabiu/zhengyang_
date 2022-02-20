# Linux下anaconda的安装




记录Linux下anaconda的安装与简单使用。

<!--more-->

## anaconda的安装
#### 下载
```bash
# 下载安装文件;请自行选择所需版本
wget -c https://repo.anaconda.com/archive/Anaconda3-2020.02-Linux-x86_64.sh
```


#### 安装
```bash
# 开始安装，中途可能会需要输入 yes/no 或默认按回车
bash Anaconda3-2020.02-Linux-x86_64.sh
```

#### 配置环境变量
```bash
# 一般会默认将Anaconda安装到PATH，如果安装中出现了问题或该选项选择了NO，就需要对环境变量进行配置
# 这里修改的是/root目录下的.bashrc，即配置的是全局变量

# 打开该文件后如果有和下面类似字样，那么就不需要配置了。

# >>> conda initialize >>>
# !! Contents within this block are managed by 'conda init' !!
	__conda_setup="$('/root/anaconda3/bin/conda' 'shell.bash' 'hook' 2> /dev/null)"
    if [ $? -eq 0 ]; then
        eval "$__conda_setup"
    else
        if [ -f "/root/anaconda3/etc/profile.d/conda.sh" ]; then
            . "/root/anaconda3/etc/profile.d/conda.sh"
        else
            export PATH="/root/anaconda3/bin:$PATH"
        fi
    fi
    unset __conda_setup
# <<< conda initialize <<<

# 如果没有类似以上内容则需要配置，在.bashrc中添加
vi ~/.bashrc
# 在文件最后加上一行，路径为所安装anaconda下的bin目录
# >>> conda initialize >>>
export PATH="/root/anaconda3/bin:$PATH"
# <<< conda initialize <<<
```

#### 刷新
```bash
# 修改文件./bashrc之后无法立即生效，需要source一下
source ~/.bashrc
# 验证是否安装成功
conda --version
>>conda 4.8.2
# 安装成功
```

## anaconda的使用
#### 创建
```bash
# 后面的python可以先不要，创建好虚拟环境后再单独安装
conda create -n your_env_name python=3.6
```
#### 查看
```bash
# 看到创建好了的虚拟环境
conda env list
```
#### 激活
```bash
# windows激活虚拟环境可以不用加前面的conda, CentOS需要加上
conda activate your_env_name
```
#### 退出
```bash
conda deactivate
```

#### 关闭开机自动进入base虚拟环境
```bash
# 环境建好后下次开机发现每次打开终端都会自动激活base虚拟环境。虽然没什么影响，但是很不爽
conda config --set auto_activate_base false
# 若需要设置为自动激活，改为true就好
```
#### 查看已安装的包
```bash
conda list
```



<div style="margin-top:2em;padding:0 1.5em;border:1px solid #d3d3d3;background-color:#f7f7f7">
    <h3>文档信息</h3>
    <ul style="padding-bottom:1.5em;">
        <li style="padding-top:0.5em;">本文作者：<a href="https://zhengyang.wang/about" target="_blank">正阳</a></li>
        <li style="padding-top:0.5em;">本文链接：<a href="https://zhengyang.wang/linux-install-anaconda" target="_blank">https://zhengyang.wang/linux-install-anaconda</a></li>
        <li style="padding-top:0.5em;">版权声明：自由转载-非商用-非衍生-保持署名（<a href="http://creativecommons.org/licenses/by-nc-nd/3.0/deed.zh" target="_blank">创意共享3.0许可证</a>）</li>
    </ul>
</div>

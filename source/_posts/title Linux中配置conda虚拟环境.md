title: Linux中配置conda虚拟环境

top: true

categories: 

- Linux

tags:

- 虚拟环境

description: <center><h3>虚拟环境配置</h3></center>

photo: http://image.mabiao.xyz/blog/20151031_124258.jpg

---

<!--more-->

- conda info -e      //查看所有的虚拟环境
- source activate your_env_name   //激活指定虚拟环境
- conda create -n your_env_name python=X.X  //创建python版本为X.X、名字为your_env_name的虚拟环境
- conda install 库名称==版本
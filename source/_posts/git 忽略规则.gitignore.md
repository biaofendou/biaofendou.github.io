title:  git 忽略规则.gitignore
categories: 

- git

tags:

- git

description: <center><h3>git在上传的时候要忽略一些配置文件和资源文件</h3></center>

photo: https://biaofendou.github.io/images/photos/ChMkJ1bKzWGIKiXhAAVxHS7pSIEAALJAQLhC9wABXE1838.jpg

---

<!-- more -->

## 在进行代码管理时，应该将（.文件）这样的环境配置文件应该忽略掉，防止每次环境变化版本出现问题，大型数据集也应该忽略

###  touch .gitignore 创建文件

### vim .gitignore  打开文件

###  在文件中加入要忽视文件的路径如 .idea/,data/等
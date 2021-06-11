### /hugo-build  No directory found
```yml
box: debian
build:
  steps:
    - arjen/hugo-build:
        version: "0.17"
        theme: herring-cove
        flags: --buildDrafts=true
        ```
        2020
版本去掉引号。
### 主题not found
Error: module "tokiwa" not found;

主题也可加到github上

### 看官方文档 
[https://devcenter.wercker.com/administration/environment-variables/creating-env-vars/](https://devcenter.wercker.com/administration/environment-variables/creating-env-vars/)

### yml 格式不要写错
$git——token 是在wercker 设置 环境那里k-v值

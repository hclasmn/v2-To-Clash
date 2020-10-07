# v2rayToClash
个人使用的v2ray订阅地址转clash的yaml的脚本

适配了 network=ws的方式

使用方法：

```bash
## 下载项目
git clone https://github.com/scjtqs/v2rayToClash
## 进入项目目录
cd v2rayToClash
## 通过composer安装依赖
composer require mustangostang/spyc
## 或者使用项目中的composer
php composer.phar require mustangostang/spyc
## 通过php脚本进行转换,修改v2c.php中的url订阅地址
php v2c.php
## 通过docker-compose启动 docker服务
docker-compose up -d
```

然后 打开浏览器 http://127.0.0.1:1234 
即可使用yacd管理clash

增加action自动化转换
```
        $url=“{{ secrets.YOURURL }}”; //你的订阅地址
```
```
        server_port: 465
        username: ${{ secrets.MAILUSERNAME }}
        password: ${{ secrets.MAILPASSWORD }}
        ${{ secrets.MAILCOM }} // 接收邮件邮箱
```
邮箱推送，可选
```
    - name: Commit
      run: |
        git config --global user.email hclasmn@qq.com
        git config --global user.name hclasmn
        git add ./ssl/
        git commit -m "Update certificate files" -a
    - name: Push
      uses: ad-m/github-push-action@master
      with:
        github_token: ${{ secrets.GITHUB_TOKEN }}
```
添加到action中yml
自动 Commit 并 Push 到本仓库.
公共仓库请删除（参考：https://www.ioiox.com/archives/104.html）


## 总览

<div class="ant-table">
<table class="downloads">
  <tbody>
    <tr>
      <td class="count" id="total-packages"></td><td>总数</td>
      <td class="count" id="total-versions"></td><td>总版本数</td>
      <td class="count" id="total-deletes"></td><td>总删除数</td>
    </tr>
    <tr>
      <td class="count"></td><td> 今日下载量</td>
      <td class="count"></td><td> 本周下载量</td>
      <td class="count"></td><td> 本月下载量</td>
    </tr>
    <tr>
      <td class="count"></td><td> 昨日下载量</td>
      <td class="count"></td><td> 上周下载量</td>
      <td class="count"></td><td> 上月下载量</td>
    </tr>
  </tbody>
</table>
</div>

<div class="sync" style="display:none;">
  <h3>Sync Status</h3>
  <p id="sync-model"></p>
  <p>Last sync time is <span id="last-sync-time"></span>. </p>
  <div class="ant-alert ant-alert-info syncing">
    <span class="anticon ant-alert-icon anticon-info-circle"></span>
    <span class="ant-alert-description">The sync worker is working in the backend now. </span>
  </div>
  <div class="ant-table">
  <table class="sync-status">
    <tbody>
      <tr>
        <td><span id="need-sync"></span> packages need to be sync</td>
        <td class="syncing"><span id="left-sync"></span> packages and dependencies waiting for sync</td>
        <td><span id="percent-sync"></span>% progress</td>
      </tr>
      <tr>
        <td><span id="success-sync"></span> packages and dependencies sync successed</td>
        <td><span id="fail-sync"></span> packages and dependencies sync failed</td>
        <td>last success: <span id="last-success-name"></span></td>
      </tr>
    </tbody>
  </table>
  </div>
</div>

<script src="/js/readme.js"></script>

## 使用
***`cnpm`不支持`package-lock.json`文件，下载的依赖包的版本跟使用npm下载的依赖版本不相同，可能造成因为版本升级导致问题，使用`npm`进行安装***

可以使用别名的方式定义不同命令使用不同的registry进行安  

```bash
alias cnpm="npm --registry=https://registry.npm.taobao.org"

#Or alias it in .bashrc or .zshrc
$ echo '\n#alias for cnpm\nalias cnpm="npm --registry=https://registry.npm.taobao.org' >> ~/.zshrc && source ~/.zshrc
```

### 安装

```bash
$ npm install [name]
```

### 同步

配置未`不同步`  
避免占用存储空间、只会存储私有的库

### 发布/取消发布
+ 设置`registry`
  + 通过上面提及的别名命令
  + 使用文件`.npmrc`
  + 在命令后加上`--registry http://localhost:xxxx/`
  + 全局设置: `npm config set registry http://localhost:xxxx/`
  + 使用nrm
    需要先安装: `npm i -g nrm`
    ```bash
    # 添加源
    $ nrm add hxq http://localhost:xxxx/
    # 切换源
    $ nrm use hxq
    ```
+ 登录npm 
  ```bash
  $ npm login
  #会提示输入帐号、密码、邮箱
  ```
+ 初始化项目  
  
  ***包名使用`@hxq`作为域控制，例如：@hxq/utils***
  ```bash
  $ npm init
  ```
+ 发布/取消发布
```bash
#发布
$ nmp publish [name]
#取消发布
$ nmp unpublish [name]
#强制删除
$ nmp unpublish -force[name]
```


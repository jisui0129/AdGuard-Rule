<div align="center">
<h1>AdGuard Rule</h1>
  <p>
    一个简易的Java程序，用于合并与更新 AdGuard 过滤规则
</p>
</div>

<p><a href="https://raw.githubusercontent.com/urkbio/AdGuard-Rule/main/rule/adgh.txt/">AdGuard Home Filter</a></p>

<p><a href="https://mirror.ghproxy.com/https://raw.githubusercontent.com/urkbio/AdGuard-Rule/main/rule/adgh.txt/">国内加速</a></p>

<h2 id="a">📔 说明</h2>

本项目旨在按需求整合 `AdGuard` 规则。定时从上游订阅获取规则，去除`重复`和`不受支持`的规则并进行分类。如果存在误杀请手动放行。  
支持`AdGuard`、`AdGuard Home`,每`12小时`自动更新一次   

#### 上游规则

<details>
<summary>点击查看</summary>
<ul>
    <li><a href="https://raw.githubusercontent.com/jdlingyu/ad-wars/master/hosts">大圣净化</a></li>
    <li><a href="https://code.gitlink.org.cn/hacamer/AdRules/raw/branch/main/adguard-full.txt">AdRules AdGuard Full List</a></li>
    <li><a href="https://raw.githubusercontent.com/AdguardTeam/FiltersRegistry/master/filters/filter_2_Base/filter.txt">adguard base</a></li>
    <li><a href="https://raw.githubusercontent.com/Lynricsy/HyperADRules/master/dns.txt">HyperADRules</a></li>
    <li><a href="https://raw.githubusercontent.com/217heidai/adblockfilters/main/rules/adblockdns.txt">adblockfilter</a></li>
    <li><a href="https://raw.githubusercontent.com/guandasheng/adguardhome/main/rule/all.txt">关圣</a></li>
    <li><a href="https://raw.githubusercontent.com/jerryn70/GoodbyeAds/master/Formats/GoodbyeAds-AdBlock-Filter.txt">Goodbyeads70</a></li>
    <li><a href="https://raw.githubusercontent.com/8680/GOODBYEADS/master/dns.txt">Goodbyeads8680</a></li>    
    <li><a href="https://adguardteam.github.io/AdGuardSDNSFilter/Filters/filter.txt">AdGuard DNS filter</a></li>
    <li><a href="https://raw.githubusercontent.com/xinggsf/Adblock-Plus-Rule/master/rule.txt">乘风 广告过滤规则</a></li>
    <li><a href="https://raw.githubusercontent.com/xinggsf/Adblock-Plus-Rule/master/mv.txt">乘风 视频过滤规则</a></li>
    <li><a href="https://raw.githubusercontent.com/o0HalfLife0o/list/master/ad.txt">HalfLife_合并自乘风视频广告过滤规则、EasylistChina、EasylistLite、CJX'sAnnoyance</a></li>
    <li><a href="https://adaway.org/hosts.txt">AdAway 官方的去广告 Host 规则</a></li>
    <li><a href="https://easylist-downloads.adblockplus.org/antiadblockfilters.txt">去除禁止广告拦截提示规则</a></li>
    <li><a href="https://raw.githubusercontent.com/Cats-Team/AdRules/main/dns.txt">杏稍AdRules DNS List</a></li>
    <li><a href="https://cdn.jsdelivr.net/gh/blackmatrix7/ios_rule_script@master/rule/AdGuard/Advertising/Advertising.txt">AdGuard_blackmatrix7合并</a></li>
    <li><a href="https://raw.githubusercontent.com/zsakvo/AdGuard-Custom-Rule/master/rule/zhihu.txt">知乎 普通版</a></li>
    <li><a href="https://raw.githubusercontents.com/timlu85/AdGuard-Home_Youtube-Adfilter/master/Youtube-Adfilter-Web.txt">Youtube-Adfilter-Web</a></li>
    <li><a href="https://raw.githubusercontents.com/91ajames/ublock-filters-ulist-youtube/main/blocklist.txt">ublock-filters-ulist-youtube</a></li>
    <li><a href="https://raw.githubusercontent.com/TG-Twilight/AWAvenue-Ads-Rule/main/AWAvenue-Ads-Rule.txt">秋风广告规则,针对Android广告</a></li>
    # uBlock内置规则
    <li><a href="https://cdn.jsdelivr.net/gh/uBlockOrigin/uAssetsCDN@main/filters/filters.txt">uBlock filters</a></li>
    <li><a href="https://ublockorigin.pages.dev/filters/badware.txt">uBlock filters – Badware risks</a></li>
    <li><a href="https://gitcdn.link/cdn/uBlockOrigin/uAssetsCDN/main/filters/privacy.txt">uBlock filters – Privacy</a></li>
    <li><a href="https://ublockorigin.github.io/uAssets/filters/quick-fixes.txt">uBlock filters – Quick fixes</a></li>
    <li><a href="https://cdn.statically.io/gh/uBlockOrigin/uAssetsCDN/main/filters/resource-abuse.txt">uBlock filters – Resource abuse</a></li>
    <li><a href="https://gitcdn.link/cdn/uBlockOrigin/uAssetsCDN/main/filters/unbreak.txt">uBlock filters – Unbreak</a></li>
    <li><a href="https://filters.adtidy.org/extension/ublock/filters/11.txt">AdGuard Mobile Ads移动设备</a></li>
    # 本地列表
    <li><a href="https://raw.githubusercontent.com/urkbio/AdGuard-Rule/main/rule/mylist.txt">mylist</a></li>
    <li><a href="https://raw.githubusercontent.com/urkbio/AdGuard-Rule/main/rule/yyy.txt">yyy</a></li>
</ul>
</details>


#### 示例配置

```yaml
application:
  rule:       
    #远程规则订阅，仅支持http、https
    remote:
      - 'https://example.com/list.txt'
    #本地规则，请将文件移动到项目路径rule目录中
    local: 
      - 'mylist.txt'
  output:
    path: rule   #规则文件输出路径，相对路径默认从 项目目录开始
    files:
      all.txt:    #输出文件名
        - DOMAIN  #域名规则，仅完整域名
        - REGEX   #正则规则，包含正则的域名规则，AdGH支持
        - MODIFY  #修饰规则，添加了一些修饰符号的规则，AdG支持
        - HOSTS   #Hosts规则
```

#### 使用 Github Action

- fork本项目
- 参照示例配置，修改配置文件: `src/main/resources/application.yml`，注意本地规则文件应放入项目根目录 `rule` 文件夹
- 编辑 `.github/workflows/auto-update.yml` 文件，将 `Commit Changes` 区块下邮箱与用户名修改为自己的（Github邮箱与用户名）
- 提交所有修改并等待 `Github Action` 执行，执行完成后相应规则生成在配置中指定的目录下


- 👉 特别感谢@fordes123

<div align='center'><a href='https://www.websitecounterfree.com'><img src='https://www.websitecounterfree.com/c.php?d=9&id=53744&s=1' border='0' alt='Free Website Counter'></a><br / ><small><a href='https://www.websitecounterfree.com' title="Free Website Counter">Free Website Counter</a></small></div>


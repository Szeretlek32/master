# JD

*************************
# [ QX 1.0.10+ 脚本配置]:
*************************

# JD历史价格

## 配置 (QuanX)

```properties
[MITM]
api.m.jd.com

[rewrite_local]
#京东历史价格
^https?://api\.m\.jd\.com/client\.action\?functionId=(wareBusiness|serverConfig|basicConfig) url script-response-body https://raw.githubusercontent.com/Szeretlek32/master/master/JD/jd_price.js
```

# JD Cookie获取

## 配置 (QuanX)

```properties
[MITM]
api.m.jd.com

[rewrite_local]
#京东获取cookie
#⚠️⚠️⚠️此为远程路径,低版本用户请自行调整为本地路径.⚠️⚠️⚠️
https:\/\/api\.m\.jd\.com\/client\.action.*functionId=signBean url script-request-header https://raw.githubusercontent.com/Szeretlek32/master/master/JD/JD_DailyBonus.js
```

## 说明

1. 先配置`[MITM]`
   - QuanX: api.m.jd.com
2. 在配置重写规则:
   - QuanX: 把`cookie`复制到相应位置并启用
3. Safari浏览器打开登录 https://bean.m.jd.com/bean/signIndex.action ,点击签到并且出现签到日历
4. 系统提示: `获取cookie: 成功`
5. 最后就可以把脚本注释掉了

> 脚本是用来获取 cookie 的, 用浏览器访问一次获取 cookie 成功后就可以删掉或注释掉了, 但请确保在`登录成功`后再获取 cookie.

## 常见问题

1. 无法写入 Cookie

   - 如果你用的是 Safari, 请尝试在浏览地址栏`手动输入网址`(不要用复制粘贴)

2. 写入 Cookie 成功, 但签到不成功

   - 看看是不是在登录前就写入 Cookie 了
   - 如果是，请确保在登录成功后，再尝试写入 Cookie

3. 为什么有时成功有时失败

   - 很正常，网络问题，哪怕你是手工签到也可能失败（凌晨签到容易拥堵就容易失败）
   - 暂时不考虑代码级的重试机制，但咱有配置级的（暴力美学）：
   
      - `QuanX`配置:

     ```properties
     [task_local]
     1 0 * * * xxx.js # 每天00:01执行一次
     2 0 * * * xxx.js # 每天00:02执行一次
     3 0 * * * xxx.js # 每天00:03执行一次

     */60 * * * * xxx.js # 每60分执行一次
     ```

## 感谢 (排名不分先后)

[@NobyDa](https://github.com/NobyDa)

[@lhie1](https://github.com/lhie1)

[@ConnersHua](https://github.com/ConnersHua)

[@sazs34](https://github.com/sazs34/)

[shylocks](https://github.com/shylocks)

[yichahucha](https://github.com/yichahucha)

[lxk0301](https://gitee.com/lxk0301)

[ChuheGit](https://github.com/ChuheGit)

[bigcandou](https://github.com/bigcandou)

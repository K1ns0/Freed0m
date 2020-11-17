# web

## 找色差吗?

查看js代码

![](../../../../assets/img/Security/CTF/writeup/2020-9-G60攻防大赛-writeup/1.png)

F12，控制台输入语句
```js
var _0x268d05 = { 'vFYyb': _0x2f2b('0x1983', 'vXeU'), 'rshMS': function _0x593385(_0x36599a, _0x5f41b7) { return _0x36599a / _0x5f41b7; }, 'xWQRG': function _0x337c99(_0x53c811, _0xe4afa4) { return _0x53c811 - _0xe4afa4; }, 'ZuQxI': function _0x242b7d(_0x4e358a, _0xbefac3) { return _0x4e358a * _0xbefac3; }, 'DCMCO': function _0x1e5dd4(_0x577f5a, _0x2dafd8) { return _0x577f5a > _0x2dafd8; }, 'bPzve': function _0x49960b(_0x43d8c9, _0x3dd75e) { return _0x43d8c9 === _0x3dd75e; }, 'GFiYI': function _0x1a3caa(_0x167948, _0x13fa0c, _0x580fa8) { return _0x167948(_0x13fa0c, _0x580fa8); }, 'rQJbg': _0x2f2b('0x1984', 'F8QA'), 'fwSPi': function _0xbc327(_0x3da5ce, _0x3e3e3c) { return _0x3da5ce(_0x3e3e3c); }, 'GkSez': '4|3|1|0|2', 'UVjif': _0x2f2b('0x1985', ']Z3^'), 'TQMlf': function _0x3c2939(_0x30791e, _0x108e7b) { return _0x30791e > _0x108e7b; } };

var _0x60a0ea = _0x268d05[_0x2f2b('0x1999', '6T2X')];

console['log'](strEnc('find_different_blocks', _0x60a0ea, '8c4f1', 'faf82'));
```
输出的字符串 md5

21E7AE40B06B28439D031D6848F6E5736B28CA5D50DB89BC34468C8195AC002AB593117A1BDAEA972B8C223883FA6443

得到flag

84673edf8a1ab819dadfdb5da4f41cfe

---

## easy upload

上传时进行 FUZZ,发现可以上传pht后缀的文件，上传一个一句话，蚁剑连接，查看flag

![](../../../../assets/img/Security/CTF/writeup/2020-9-G60攻防大赛-writeup/2.png)

![](../../../../assets/img/Security/CTF/writeup/2020-9-G60攻防大赛-writeup/3.png)

---

# Misc

## 巨人的秘密

binwalk 跑一下发现有 zip 在里面,直接用 winrar 修复出来,然后改一下后缀名为 zip

![](../../../../assets/img/Security/CTF/writeup/2020-9-G60攻防大赛-writeup/7.png)

![](../../../../assets/img/Security/CTF/writeup/2020-9-G60攻防大赛-writeup/8.png)

通过 010 editor 将图片从图片源文件另存出来并压缩成 zip,确保 CRC 一致

![](../../../../assets/img/Security/CTF/writeup/2020-9-G60攻防大赛-writeup/9.png)

![](../../../../assets/img/Security/CTF/writeup/2020-9-G60攻防大赛-writeup/10.png)

然后进行明文攻击

![](../../../../assets/img/Security/CTF/writeup/2020-9-G60攻防大赛-writeup/11.png)

![](../../../../assets/img/Security/CTF/writeup/2020-9-G60攻防大赛-writeup/12.png)

结合 010 里看到的 DeEgger 可知是 DeEgger Embedder 隐写

解密

![](../../../../assets/img/Security/CTF/writeup/2020-9-G60攻防大赛-writeup/13.jpg)

根据主办方给出的工具 PixelJihad，用密码 Wings_of_freedom 成功解出

![](../../../../assets/img/Security/CTF/writeup/2020-9-G60攻防大赛-writeup/14.png)

---

# 创新组

## blueshark

binwalk 发现了一个 7z 的压缩包，直接当成压缩包打开，发现有个 password_is_Bluetooth_PIN.txt文件

![](../../../../assets/img/Security/CTF/writeup/2020-9-G60攻防大赛-writeup/4.png)

![](../../../../assets/img/Security/CTF/writeup/2020-9-G60攻防大赛-writeup/6.png)

Ctrl + F，选择 分组详情 或者 分组列表，字符串 或者 正则表达式，搜 pin。

![](../../../../assets/img/Security/CTF/writeup/2020-9-G60攻防大赛-writeup/5.png)

PIN 就是 141854。

用来解压就可以得到 flag。

6da01c0a419b0b56ca8307fc9ab623eb

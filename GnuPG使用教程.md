GnuPG使用教程
====
###生成密钥   
使用以下命令生成自己的密钥：   

>gpg --gen-key   

1.会出现一大段文字：先是关于软件的介绍和一些版权信息，然后询问你选择哪种加密算法，我选择默认的RSA and RSA，因为目前来说，`RSA`算法是安全性最强的。   
2.然后询问你密钥长度，我选择最长的`4096`   
3.接下来询问你密钥的有效期，默认值0代表永不过期，我选择默认值   
4.接下来会让你确认一下是否正确。   
输入y确认之后，要求你输入个人信息，软件通过真实姓名、注释和Email地址来构造用户ID，其中注释可以为空。   
5.然后用户ID就生成了，软件会向你确认信息是否需要修改：输入N修改姓名，C修改注释，E修改Email，O表示确认，Q退出。我输入字母o确认。   
6.之后会要求你输入一个口令用以保护你的私钥，强烈建议添加口令！   
7.然后软件说“需要生成大量随机字节”，你可以随意进行一些操作，看看网页啊，打打字什么的，“这会得到足够的熵”(熵在物理学中是微观状态混乱度的度量)。   
8.现在，你的公、私钥已经生成并签名！   
9.最后，建议再生成一个撤销证书，以便以后密钥作废时，请求公钥服务器撤销你的公钥：    
>gpg --ken-revoke [用户ID]   

##密钥管理

###列出密钥
>gpg --list-keys

###删除密钥
>gpg --delete-key [用户ID]                   # 删除公钥
>gpg --delete-secret-keys [用户ID]           # 删除私钥

###导出密钥
公钥和私钥都是以二进制形式存储，使用armor参数可以导出为ASCII码形式。(wilson是用户ID)
>导出公钥：gpg --armor --output public.key --export wilson
>导出私钥：gpg --armor --output private.key --export-secret-keys wilson

###导入密钥
>gpg --import [密钥文件]                 # 从密钥文件导入
>gpg --keyserver hkp://subkeys.pgp.net --search-keys [用户ID] # 从密钥服务器导入

###上传公钥
>gpg --send-keys [用户ID] --keyserver hkp://subkeys.pgp.net

##加解密

###加密
--recipient参数后跟对方的用户ID；--output参数后面跟导出的文件名；--encrypt参数后跟要加密的文件。
这里应该注意一个问题，就是你要确定你使用的公钥的可靠性。
>gpg --recipient wilson --output GPG_1 --encrypt 1.txt

添加--armor导出为ASCII码形式
>gpg --recipient wilson --armor --output GPG_1 --encrypt 1.txt

###解密
然后用我自己的私钥解密：
>gpg [文件名]

解密文件并从命名
>gpg --decrypt en_1 > ww.txt

--decrypt参数后跟要解密的文件，然后我这儿用了重定向将解密结果重定向到名为vps的文件中，否则解密结果会直接输出到屏幕。有的介绍说使用--output参数后跟导出文件名，但是我的笔记本上不可以，不知道为什么嗯...

###签名
有时，我们不需要加密文件，只需要对文件签名，表示这个文件确实是我本人发出的。sign参数用来签名。
>gpg --sign test.txt

然后生成了一个test.txt.gpg文件，我们打开这个文件后，发现这也是一个二进制的数据，这并不是加密后的数据，与上边的二进制数据不一样。如果想生成ASCII码的签名文件，可以使用clearsign参数
>gpg --clearsign test.txt

然后生成了一个test.txt.asc文件
如果想生成单独的签名文件，与文件内容分开存放，可以使用detach-sign参数。
>gpg --detach-sign test.txt

是一个二进制的数据，如果想采用ASCII码形式，要加上armor参数
>gpg --armor --detach-sign test.txt

###帮助
>gpg --help

支持的算法：
公钥：RSA, RSA-E, RSA-S, ELG-E, DSA
对称加密：IDEA, 3DES, CAST5, BLOWFISH, AES, AES192, AES256,
               TWOFISH, CAMELLIA128, CAMELLIA192, CAMELLIA256
散列：MD5, SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
压缩：不压缩, ZIP, ZLIB, BZIP2

语法：gpg [选项] [文件名]
签名、检查、加密或解密
默认的操作依输入数据而定

###指令
| 指令   |                          |                                    |
| ------ | ------------------------ | ---------------------------------- |
| -s     | --sign [文件名]          | 生成一份签名                       |
|        | --clearsign [文件名]     | 生成一份明文签名                   |
| -b     | --detach-sign            | 生成一份分离的签名                 |
| -e     | --encrypt                | 加密数据                           |
| -c     | --symmetric              | 仅使用对称加密                     |
| -d     | --decrypt                | 解密数据(默认)                     |
|        | --verify                 | 验证签名                           |
|        | --list-keys              | 列出密钥                           |
|        | --list-sigs              | 列出密钥和签名                     |
|        | --check-sigs             | 列出并检查密钥签名                 |
|        | --fingerprint            | 列出密钥和指纹                     |
| -K     | --list-secret-keys       | 列出私钥                           |
|        | --gen-key                | 生成一副新的密钥对                 |
|        | --delete-keys            | 从公钥钥匙环里删除密钥             |
|        | --delete-secret-keys     | 从私钥钥匙环里删除密钥             |
|        | --sign-key               | 为某把密钥添加签名                 |
|        | --lsign-key              | 为某把密钥添加本地签名             |
|        | --edit-key               | 编辑某把密钥或为其添加签名         |
|        | --gen-revoke             | 生成一份吊销证书                   |
|        | --export                 | 导出密钥                           |
|        | --send-keys              | 把密钥导出到某个公钥服务器上       |
|        | --recv-keys              | 从公钥服务器上导入密钥             |
|        | --search-keys            | 在公钥服务器上搜寻密钥             |
|        | --refresh-keys           | 从公钥服务器更新所有的本地密钥     |
|        | --import                 | 导入/合并密钥                      |
|        | --card-status            | 打印智能卡状态                     |
|        | --card-edit              | 更改智能卡上的数据                 |
|        | --change-pin             | 更改智能卡的 PIN                   |
|        | --update-trustdb         | 更新信任度数据库                   |
|        | --print-md 算法 [文件]   | 使用指定的散列算法打印报文散列值   |

###选项
| 选项   |                          |                                    |
| ------ | ------------------------ | ---------------------------------- |
| -a     | --armor                  | 输出经 ASCII 封装                  |
| -r     | --recipient 某甲         | 为收件者“某甲”加密                 |
| -u     | --local-user             | 使用这个用户标识来签名或解密       |
| -z     | N                        | 设定压缩等级为 N (0 表示不压缩)    |
|        | --textmode               | 使用标准的文本模式                 |
| -o     | --output                 | 指定输出文件                       |
| -v     | --verbose                | 详细模式                           |
| -n     | --dry-run                | 不做任何改变                       |
| -i     | --interactive            | 覆盖前先询问                       |
|        | --openpgp                | 行为严格遵循 OpenPGP 定义          |
|        | --pgp2                   | 生成与 PGP 2.x 兼容的报文          |
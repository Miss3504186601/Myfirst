---
theme: channing-cyan
highlight: a11y-dark
---
# DID 本地简单实现简述
## 一、json文档介绍
形如：
```
**// 上次更新时间
**    "updated" :
```
为本人设计的文档未加入但别人文档中包含的字段，作为补充
### 1.doc

```json
 {
    // 所遵循的JSON-LD标准
    "@context": [
        "https://w3id.org/diot/v1"
    ],
    // 文档的 `DIOT`
    "id":"did:diot:0821C9j91uvgapv4xZGQ",
    // 创建时间
    "created": "2024-04-19T20:22:02.438572",
    // 上次更新时间
    "updated": "2024-04-19T20:22:02.438572"，
    // 版本号，用于文档更新
    "version": 1,
    // 公钥
    "publicKey": [
        {
            // 公钥的id
            "id": "did:diot:0821C9j91uvgapv4xZGQ"#key-1",
            // 公钥的加密算法类型
            "type": "RsaVerificationKey2018",
            // 一个 `DIOT`，表明此公钥的归属。
            "controller": "did:diot:0821C9j91uvgapv4xZGQ"
            // 公钥的十六进制编码
            "publicKeyHex": "2d2d2d2d2d424547494e205055424c4943204b45592d2d2d2d2d0a4d494942496a414e42676b71686b6947397730424151454641414f43415138414d49494243674b43415145416e434d52462f6374507776306350496243644d710a51743259456b4c6c6c52474b557641746a7764436236342f5862394c6477796a47385547595a536f4d536b673364324a6d5739744c484a447a676842767959720a6f426975763241494a6d57427751444862564f2b786d45576d513876506166737076712b6b4f6d43546c53586f6d7266554531365053327a4e496332447838410a59444f7744506b2f70476763744449484c50735436706e4e727059694d6a54682b696b496a734c63637a614d7a67514862546e4e663575513733706a385a58770a5048796837646169596c554443675a653569784841366c756f7979757369662f7950696633464c4e774553774264725361343932654a6e556f745a46536351730a7a7a587758716a7a7258344c4c6a757a5949496e6b58574d7a6b73657035795930416f6e39433337782f33737669464c6f4b6f643733426a67533077496169700a77774944415141420a2d2d2d2d2d454e44205055424c4943204b45592d2d2d2d2d0a"
        },
        {
            // 一个 `DIOT`，表明此公钥的归属。
            "id": "did:diot:0821C9j91uvgapv4xZGQ#key-2",
            // 公钥的加密算法类型
            "type": "EcdsaVerificationKey2018",
            // 公钥的归属，一个did标识
            "controller": "did:diot:0821C9j91uvgapv4xZGQ"
            // 公钥的十六进制编码
            "publicKeyHex": "2d2d2d2d2d424547494e205055424c4943204b45592d2d2d2d2d0a4d494942496a414e42676b71686b6947397730424151454641414f43415138414d49494243674b4341514541716a58504e51525441477344556c4c73624c524c0a3856434a646475704932396c74366944383253307a7a70392f4d516c343236715346767749667769746a4f4c4a51726c65594c58666e35536a456234524b44530a444c546561636d4a5933592f784a343858627036466b7935746a6f6f76694b507862384f596c795a3042427565734f4333566148416b2b476a444d466b79702f0a6b6d6244475067796b696f4e5a634d6a622b45334271784777415a70324c4350446d31736247434732546979683257513434385658477332744b384b524650750a42705a783663376d3262643161586d6c6f496661354e367a7a766e396f2b34552b4b4559516d415636506d7351704f4f335574315861695a62666b7a68324d570a4653767448455863744b766154744e2f566f52633168384d504a31727933616c69533541544e4a4847686c53504b3935387577466f6d654f4943794872714f450a44514944415141420a2d2d2d2d2d454e44205055424c4943204b45592d2d2d2d2d0a"
        }
    ],
    // 一组公钥的 `DIOT`，表明此 `DIOT` 的归属，拥有此公钥对应私钥的一方可以控制和管理此 `DIOT` 文档。
    "authentication": [
        "did:diot:0821C9j91uvgapv4xZGQ#key-1"
    ],
    // 一组和本 `DIOT` 相关联的其他 `DID`
    **"alsoKnownAs" :[
    **   // 关联标识的类型
    **   "type":
    **  // 关联的标识
    **  "id" :
    // 一组公钥 `id`,在 `authentication私钥` 泄漏或者丢失的情况下用来恢复对文档的控制权。
    "recovery": [
        "did:diot:0821C9j91uvgapv4xZGQ#key-2"
    ],
    **// 一组子链 `AC` 号，只有 `DIOT` 文档类型不是凭证类型且文档是主链上的 `BID` 文档才可能有该字段，存放当前BID拥有的所有 `AC` 号。
    **"acsns" :
    **// 凭证列表
    **"verifiableCredentials" :[{
    **  // 可验证声明的DIOT
    **  "id":
    **  // 凭证类型
    **  "type" :},
    **  ...]
    // 一组服务地址
    "service": [
        [
            {
                // 服务地址的 `id`
                "id": "did:diot:0821C9j91uvgapv4xZGQ#resolver",
                // 字符串，代表服务的类型
                "type": "DIDResolve",
                // 一个 `URI` 地址
                "serviceEndpoint": "https://did.studyzydemo.com"
            }
        ]
    ],
    // 文档所有者对文档内容的签名
    "proof": {
        // 私钥加密算法类型
        "type": "RsaVerificationKey2018",
        // 创建日期
        "created": "2024-04-19T20:22:02.438572",
        // proof的创建者，这里是一个公钥的 `id`
        "creator": "did:diot:0821C9j91uvgapv4xZGQ",
        // 使用相应私钥对除 `proof` 字段的整个diot文档签名
        "signatureValue": "084b4a6865c0ee9a66d30e601331c2d482c5b8de6cd5104c052a6ed8cd43a81e72efdd0ba54323db2316adf7fae4c834aa73cda50ebe91435acf64a40218cf4e3d04fd75ac30bf177367c91fea404e3fc013aaa3d14cc85f0b21d10344b6a91f5fc7fb26e54d5a6bd99375162146b6e83a14e19e53e7ca6dc47bfa99777f0d9bd5280d2c3344094384354148567c6084e8cf5b5d4a112e71bcba953bc1a8ceb37cba793db9bec51b48f80f8807a309b850b3fa177fb9e21dccf2df118ec430c74a7934d3f953371e4e7a938dc4f9129b8f3210a54db56f8e2c25d54a6994a647add8a8aa0c136e98144bc33fb43754de53c38678b9cac57de3bfd7daa717857a"
    }
}
```
### 2.vc
```json
{
    // VC内容所遵循的JSON-LD标准
    "@context": [
        "https://www.w3.org/2018/credentials/v1",
        "https://www.w3.org/2018/credentials/examples/v1"
    ],
    **// 本VC的唯一标识，也就是证书ID
    **"id" :
    // VC内容的格式
    "type": [
        "VerifiableCredential",
        "AlumniCredential"
    ],
    // 本VC的发行人
    "issuer": "did:diot:08269ZbXcNZrJLonbh8D",
    // VC声明的具体内容
    "credentialSubject": {
        "name": "小明",
        // 声明的断言内容
        "alumniOf": {
            "name": [
                {
                    "value": "电子科技大学",
                    "lang": "cn"
                }
            ],
            "id": "did:diot:08269ZbXcNZrJLonbh8D"
        },
        "degree": "硕士研究生",
        "degreeType": "工科",
        "college": "计算机学院",
        // 被声明的人的DID
        "id": "did:diot:0821qYVQnQWqBAkGiuru"
    },
    // 本VC的发行时间
    "issuanceDate": "2024-04-19T20:22:02.447575",
    // 对本VC的证明
    "proof": {
        // proof的创建者，这里是一个公钥的 `id`
        "creator": "did:diot:08269ZbXcNZrJLonbh8D#keys-1",
        // 签名创建时间
        "created": "2017-06-18T21:19:10Z",
        // 本证明的目的
        "proofPurpose": "assertionMethod",
        **// 验证本签名的公钥的ID**
        **"verificationMethod": "https://example.edu/issuers/keys/1",**
        // 私钥加密算法类型
        "type": "RsaVerificationKey2018",
        // 使用相应私钥对除 `proof` 字段的整个VC文档签名
        "signatureValue": "97b30de9c2efe1426d780256fb75bf5d1a272e391e0e95ac8f056ea2aeca64eb9aa46420b1f65f1ab83dd1250dc0c33625e05adbbb8439a6c480518687d2595f98dc675adcb43a3707bafebbb38ebc18214a996bfd11449890fb21c8b0c79bd619cbc0f6f35e15e4637435cffde5379cd839e6812171b7aa81e70216b7b00ee8754c6dfb500e6a6f9c8568ab9e49fa4c6bdd2edde43e5303b2e064de8214efbc3a51008eedf4d8ae05db4fc6d9062feda9beef98c3371e2485ea5f07521287ab1647646c380d638e6f20de62373715ea61d1a40cb62b9b7a2fdcab6531f77cf549c557764aa402cd59921b48de762fb9449e732c5109ecf7e3244114beff7fc6"
    }
}
```
### 3.vp

```json
{
    // VP内容所遵循的JSON-LD标准
    "@context": [
        "https://www.w3.org/2018/credentials/v1",
        "https://www.w3.org/2018/credentials/examples/v1"
    ],
    // 对本VP的证明
    "proof": {
        // 私钥加密算法类型
        "type": "RsaSignature2018",
        // 创建时间
        "created": "2024-04-19T20:22:02.450573",
        // 本证明的目的
        "proofPurpose": "authentication",
        // 验证本签名的公钥的ID
        "verificationMethod": "did:diot:0821qYVQnQWqBAkGiuru#keys-1",
        // challenge和domain是为了防止重放攻击而设计的
        "challenge": "1f44d55f-f161-4938-a659-f8026467f126",
        "domain": "4jt78h47fh47",
        // 使用相应私钥对除 `proof` 字段的整个VP文档签名
        "jws": "719259560b48196b64f2febeb594cb6ca0b77884a129f2d2454381bce1f99b7fc7505637e0b03fb6ff8bfbb70a42417ce477d53802f3f51c5e51a7670f79379297a4eaa548802a66db62f509856cbad62867ae058e8481ee9cc8c191c2bd717cb19c051b4e3ad4dd0b6d870e494183838c257d2df8f2792ef3a0754b8727329951c7544348cec046efb80a0d61d2056a0e29ce9af8390c542d26f1092e006bda5ecf3793477f58d8011089947c5ab5d80fec1caa075c2ead5ab2dbcf4f5cfc45b21d3d4c4c2f8e3ed355fa8ee5902cd7418b8791f38d7775cc4a86710e4047988d9636c83d01846db0e8af79b5fc7b26b7e38aa0fe2f215a3c2aabc828e60134"
    },
    // 文档类型
    "type": "VerifiablePresentation",
    // 本VP包含的VC的内容
    "verifiableCredential": {
        // VC内容所遵循的JSON-LD标准
        "@context": [
            "https://www.w3.org/2018/credentials/v1",
            "https://www.w3.org/2018/credentials/examples/v1"
        ],
        **// 本VC的唯一标识，也就是证书ID
        **"id" :
        // VC内容的格式
        "type": [
            "VerifiableCredential",
            "AlumniCredential"
        ],
        // 本VC的发行人
        "issuer": "did:diot:08269ZbXcNZrJLonbh8D",
        // VC声明的具体内容
        "credentialSubject": {
            "name": "小明",
            // 声明的断言内容
            "alumniOf": {
                "name": [
                    {
                        "value": "电子科技大学",
                        "lang": "cn"
                    }
                ],
                "id": "did:diot:08269ZbXcNZrJLonbh8D"
            },
            "degree": "硕士研究生",
            "degreeType": "工科",
            "college": "计算机学院",
            // 被声明的人的DID
            "id": "did:diot:0821qYVQnQWqBAkGiuru"
        },
        // 本VC的发行时间
        "issuanceDate": "2024-04-19T20:22:02.447575",
        // 对本VC的证明
        "proof": {
            // proof的创建者，这里是一个公钥的 `id`
            "creator": "did:diot:08269ZbXcNZrJLonbh8D#keys-1",
            // 签名创建时间
            "created": "2017-06-18T21:19:10Z",
            // 本证明的目的
            "proofPurpose": "assertionMethod",
            **// 验证本签名的公钥的ID**
            **"verificationMethod": "https://example.edu/issuers/keys/1",**
            // 私钥加密算法类型
            "type": "RsaVerificationKey2018",
            // 使用相应私钥对除 `proof` 字段的整个VC文档签名
            "signatureValue": "97b30de9c2efe1426d780256fb75bf5d1a272e391e0e95ac8f056ea2aeca64eb9aa46420b1f65f1ab83dd1250dc0c33625e05adbbb8439a6c480518687d2595f98dc675adcb43a3707bafebbb38ebc18214a996bfd11449890fb21c8b0c79bd619cbc0f6f35e15e4637435cffde5379cd839e6812171b7aa81e70216b7b00ee8754c6dfb500e6a6f9c8568ab9e49fa4c6bdd2edde43e5303b2e064de8214efbc3a51008eedf4d8ae05db4fc6d9062feda9beef98c3371e2485ea5f07521287ab1647646c380d638e6f20de62373715ea61d1a40cb62b9b7a2fdcab6531f77cf549c557764aa402cd59921b48de762fb9449e732c5109ecf7e3244114beff7fc6"
        }
    }
```
## 二、 流程解释  
**流程图**


![DID.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/9d54c0cde8cc41588c477c540e000076~tplv-k3u1fbpfcp-jj-mark:0:0:0:0:q75.image#?w=1765&h=1011&s=99425&e=png&b=ffffff)
### 基础层
#### 1.did初始化，doc生成
   通过用户基本属性（用户类型、加密算法类型、hash算法类型）生成特定did标识符
> ***储存结构***  
> 在 diot 方法中，可验证数据注册表维护二级映射字典树的结构。其中，一级映射为 DID 方法到存储区的映射，具体为方法名到第二级 map 结构的起始地址映射。由于 diot 方法将物 联网系统中的实体分为组织、个人、设备、物体四类，第二级映射表结构中将类型名映射到 不同的字典树，以根据特定标识符导引至不同的存储区域，实现更高的检索效率。  
> diot 中的 DID 是由 29 个字符组成的字符串，其中方法特定标识符为 20 字符长度，除去 4 字符的类型 表示，剩余 16 字符作为由 DID 映射到 DIDDoc 的索引结构。该字典树共 16 层，每个节点的 子节点数固定为 58，DID 方法特定标识符后 16 位按从左至右的顺序对应到字典树中的根节 点至叶子结点，叶子结点指向 DIDDoc 地址。根据上述结构，可验证数据注册表根据 DID 检 索 DIDDoc 的效率可以稳定保持 O(1)，同时插入、删除的效率也为 O(1)  

![image.png](https://p6-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/1ccf03ddf6af4966a75ea6fd5c948cf5~tplv-k3u1fbpfcp-jj-mark:0:0:0:0:q75.image#?w=900&h=592&s=222097&e=png&b=fefafa)  
> **生成方法**  
> ```
> 步骤 1：基于随机种子seed生成随机数作为私钥 
> 步骤 2：生成公私钥对  
> 步骤 3：与可验证数据注册表建立连接，进行系统时间同步，获得时间戳 T；  
> 步骤 4：计算公钥 Kpub 哈希 h0  
> 步骤 5：提取步骤 4 所得到的公钥生成哈希值前 20 字节得到 h0’  
> 步骤 6：添加 DID 方法名 did:diot、时间戳 T、实体 idtype 以及本机 MAC 地址至步骤 5 的 h0 得到 h1  
   h1 = (d<sub>n</sub>|T|id|T|m)  
   dn 代表 DID 方法名，id 代表 idtype，m 代表执行生成操作的设备 MAC 地址  
> ```
> 步骤 7：对步骤 6 得到的 h1 进行哈希计算得到哈希值 h2  
> 步骤 8：使用比特币 Base58 算法对 h2 进行编码得到 e’，长度为 L  
> 
> 步骤 9：在步骤 8 得到的 e’中随机取 16 位得到子串 e：   
>       𝑛 = 𝑅(𝑠𝑒𝑒𝑑)   
>       𝑖 = 𝑛 mod (𝐿 − 16)    
>       𝑒 = 𝑆(𝑒 ′ , 𝑖, 16)   
>    n 是基于随机种子值 seed 得到的随机整数，i 为 n 对 L-16 取模得到 的值，S 为自索引 i 位置截取 16 位字符  
>    
> 步骤 10：将 16 位二进制 idtype 编码为 4 字符长度的十六进制字符添加至 e 串头部，并 添加 DID 方法固定前缀，得到最终 DID：   
>       𝑑𝑖𝑑 = (𝑡𝑒 + 𝐸𝑝 + 𝐻 + 𝑒)   
> te 代表实体类型编号，Ep 代表签名算法编号，H 代表哈希算法编号。

*注：diot方法为笔者引用，并非原创。*

   紧接着生成用户的doc
#### 2. 解析器初始化，储存doc
通过用户did标识符生成专属的解析器，完成doc的储存
### 应用层
#### 1. issuer颁发vc,用户生成vp
根据issuer确定的vc内容，通过Holder解析器生成用户的专属vc
根据Holder确定的vp内容，通过Holder解析器生成特定vp
#### 2. 通过用户解析器获取用户doc
#### 3. 核验Holder提供的vp
   在Holder提交的vp中获得Holder公钥十六进制字符、Holder的vc、Holder对vp的私钥签名
   
   
通过vc获得issuer的did、issuer对vc的私钥签名

通过issuer的did获取issuer的doc，从issuer的doc中获得issuer公钥十六进制字符、Manager(issuer的doc创建者）的did

用issuer公钥对Holder——vc验证未被修改

用Holder公钥验证vp未被修改  
#### 信誉更新  

```js  

```
## 三、readme
###  模块class
#### 1.类Node
##### 数据属性：
*reputation_threshold_value*信誉阈值  
*did, 公私钥， vc， vp*


*idtype, signature_type, hash_type*用于生成did标识符


*vc_version, vp_version*记录文档版本

*path*用户信息储存路径  
*score_from_holder，score_from_issuer，score_sum，reputation_data*与信誉更新有关的数据

##### 方法、函数：

构造函数：

```js
参数--> idtype, signature_type, hash_type或者did标识符
功能--> 初始化密钥并储存
        初始化did标识符
        初始化储存路径
返回值--> 无
```

create_DID_doc

```
参数-->None
功能-->生成用户doc文档
返回值-->doc字典
```
create_VP
```
参数-->vp内容
功能-->生成vp
返回值-->vp 字典
```
create_vc
```
参数-->vc内容
功能-->生成vc
返回值-->vc 字典
```
#### 2.派生类Issuer
新数据属性：无

新函数：create_doc
```
参数：无
功能：生成Issuer的doc
返回值：doc字典
```
#### 3.派生类Manager
新数据属性：doc（记录自身doc）
新函数：check_vp
```
参数：vp字典
功能：检验vp是否有效
      若vp有效，打印“VP is valid”
      否则打印“VP is invalid”
返回值：无
```
### 模块Functions
包含一些处理函数
#### 1.create_rsa_key
```
参数：无
功能：生成rsa密钥
返回值：公钥、私钥、公钥pem、私钥pem、公钥十六进制字符串，字典形式
```
#### 2.private_key_hex_sign
```
参数：待签名的字符串、私钥对象
功能：用私钥对信息签名
返回值：十六进制签名字符串
```
#### 3.hash_message
```
参数：待签名字符串
功能：对信息取hash值
返回值：信息的十六进制hash值
```
#### 4.pub_and_pri_proof
```
参数：信息的字节、签名的十六进制字符串、对应的公钥十六进制字符串
功能：公钥对私钥签名验证
      若验证成功，打印“Signature is valid”
      否则打印“Signature is invalid”
返回值：无
```
### 模块Parser
具有但不局限于解析器的功能，以类的形式存在
#### 1.数据属性
```
holder_did：用户did标识符
directory_path:用户文档储存路径
method_name,idtype,idtype_hex,idtype_bin,signature_bin,hash_bin idstring:确定directory_path
```
#### 2.函数
构造函数
```
参数：did标识符字符串
功能：生成directory_path
返回值:无
```
add_vc
```
参数：vc字典
功能：储存vc
    若vc已经存在，打印“The vc has already been added.Addition fails.”
    否则打印“The vc has been added successfully.”
返回值：无
```
get_vc
```
参数：无
功能：获取vc
    若vc不存在，打印The vc did does not exist
返回值：vc字典
```
add_doc
```
参数：doc字典
功能：储存doc
    若doc已经存在，打印“The document already exists, addition fails.”
    否则打印“The doc has been added successfully.”
返回值：无
```
get_doc
```
参数：无
功能：获取doc
    若doc不存在，打印The doc did does not exist
返回值：doc字典
```
add_vp
```
参数：vp字典
功能：储存vp
    若vp已经存在，打印“The vp already exists, addition fails.”
    否则打印“The vp has been added successfully.”
返回值：无
```
get_vp
```
参数：无
功能：获取vp
    若vp不存在，打印The vp did does not exist
返回值：vp字典
```



    





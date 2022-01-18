### Basis of Encryption

#### Hash function

1. Properties for encryption hash functions 

   - Collision resistance[or Collision free]
     - 一般用作加密的哈希函数，都具有难以认为制造碰撞的特性，也就是难以用特定的方式得到哈希碰撞
     - MD5 码已经由当初的安全变为了可人工制造碰撞
     - 是实践经验，并不能进行严格的数学证明
   - Hiding
     - 顾名思义，是隐藏信息，指隐藏了原信息，而只向公众展示哈希结果
     - 并且哈希结果难以逆向得出，通常唯一可能得到原始信息的方式是暴力破解，即Brute Force
     - 选择安全的哈希函数，使暴力破解的概率微乎其微
   - Puzzle friendly[additional for Bit-coin]
     - 对于比特币每个区块的哈希码的前几位保证多少位0等即满足某种要求**H(blocker header[nonce]) <= target**
     - 保证了工作量的有效性，证明做出了足够的工作量
     - 寻找nonce的挖矿过程很困难，很繁琐，但是一旦nonce被试探出，验证是很容易的【hard to find, yet easy to verify】

   Collision resistance + hiding实现了Digital commitment[digital equivalent of **a sealed envelope**]

   进行预测时如何验证预测的准确性：

   1. 保证预测在结果出现之前做出

   2. 不能公开预测【公开可能会对结果产生影响，如股神巴菲特的话可能会影响人们的选择，或顺从或违背】

   3. 封装后交由第三方机构防止纂改

      以上三点就是保证预测有效的 sealed envelope

2. 一般哈希函数应具有的特性

   - 一般足够大的取值空间【若取值空间十分有限，如股票有多少支，那么在这种情况下可以采用增加随机字串nonce的方法来补充位数】H(x||nonce)
   - 每种取值的可能性从概率上应该相近，不应该有特别突出的取值

#### Signature

比特币作为一种去中心化的数字货币，没有如银行等机构，故每个用户的账户都是本地随即生成的【公钥+私钥】 非对称加密

- 公钥——银行卡号
  - 公开，任何人都可以知道
  - 通过公钥可以进行交易
- 私钥——取款密码
  - 保存在本地，一旦丢失，无法找回，账户无法使用
  - 暴力破解私钥不太可能
  - 产生相同的公钥与私钥组合的概率更比地球爆炸的概率更低


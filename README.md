一，	md5校验
1，	原理
MD5即Message-Digest Algorithm 5（信息-摘要算法5），用于确保信息传输完整一致。是计算机广泛使用的杂凑算法之一（又译摘要算法、哈希算法），主流编程语言普遍已有MD5实现。将数据（如汉字）运算为另一固定长度值，是杂凑算法的基础原理，MD5的前身有MD2、MD3和MD4。广泛用于加密和解密技术，常用于文件校验。校验？不管文件多大，经过MD5后都能生成唯一的MD5值。好比现在的ISO校验，都是MD5校验。怎么用？当然是把ISO经过MD5后产生MD5的值。一般下载linux-ISO的朋友都见过下载链接旁边放着MD5的串。就是用来验证文件是否一致的。
	2，MD5算法特点：
①、压缩性：任意长度的数据，算出的MD5值长度都是固定的。
②、容易计算：从原数据计算出MD5值很容易。
③、抗修改性：对原数据进行任何改动，哪怕只修改1个字节，所得到的MD5值都有很大区别。
④、弱抗碰撞：已知原数据和其MD5值，想找到一个具有相同MD5值的数据（即伪造数据）是非常困难的。
⑤、强抗碰撞：想找到两个不同的数据，使它们具有相同的MD5值，是非常困难的。
MD5的作用是让大容量信息在用数字签名软件签署私人密钥前被”压缩”成一种保密的格式（就是把一个任意长度的字节串变换成一定长的十六进制数字串）。除了MD5以外，其中比较有名的还有sha-1、RIPEMD以及Haval等。
2，	应用
我利用md5校验校检u盘文件与拷贝后文件的md5值，在通过代码进行对比。
String md = sd.md5sum(String.valueOf(a.get(i)));
String sgou = sd.md5sum(String.valueOf(b.get(i)));
link.add(md);
connect.add(sgou);
if (md.equals(sgou)) {
    Log.i(TAG, "相同");


二，	U盘的文件拷贝及校验
1，	设计原理
遍历整个u盘目录，如果是文件夹就继续遍历，如果是文件就复制。校验即利用md5值，将遍历来的文件取md5值，再将拷贝后的文件取md5值。因为文件不止一个，所以我将MD5值分别传入两个集合中，并排序，最后一个个进行对比，并用log打印，不同就弹窗指出哪个路径报错。
2，	UI界面
利用两个recycleview形成两个竖向的可滑动的控件。
 
3，困惑及解决方法
 
生命周期中未将application初始化，应该将继承的类在清单文件中表示。
 
主线程耗时太多，可能造成ANR
所以应当采用子线程分担压力。
 

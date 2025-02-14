# SiglusEngie Tools

主体照着number201724的代码抄来的，压缩函数参照了Xmoe的代码。

otherTools里是 https://github.com/marcussacana/SiglusSceneManager 的工具，
可以直接编辑ss和dbs（不推荐）。
主要的是用它来搜索Key。

处理Scene和Gameexe需要把Decryption.py里面的key改成目标游戏的Key，默认的是“神待ちサナちゃん　DL版”。

外挂了C++来处理，速度得到了飞跃性的提升（谜之声：那干嘛不直接用C写？——别闹，py才是灵魂啊！）

ScenePacker用-c调用压缩函数，压缩等级2-17，默认为最高17（因为实际上速度差不了多一点）。不加-c使用伪压缩。

GameexePacker同样支持-c，-p控制是否二次加密（大致测试并无影响）。

dbs也用上了C++，-c压缩参数同上。

增加用于移动端的pck封装文件的解包封包功能。

Dumper进行了文本过滤，过滤掉了纯英文的行，
dbsDecrypt过滤掉了空行和数字。

整体优化了代码， 现在可以用其他py调用。
调用函数main(argv,key)或main(argv)。
输入变量都是list。key为空list时使用默认Key。

GUI基本完善，最后一次使用的Key会储存在SiglusKey.txt里，删除该文件恢复默认Key。

GUI增加已知Key选择功能，如果存在KeyList.txt会读取其中的Key并以下拉列表形式出现。
选择了已知Key将不会保存SiglusKey.txt。

***
## Usage:
```
SceneUnpacker.py <Scene.pck> [Scene\]
ScenePacker.py <Scene.pck> <Scene\> [Scene.pck2] [-c [2~17]]

GameexeUnpacker.py <Gameexe.dat> [Gameexe.ini]
GameexePacker.py <Gameexe.ini> [Gameexe.dat2] [-p] [-c [2~17]]

ssDumper.py <Scene\> [text\]
ssPacker.py <Scene\> <text\> [output\]

dbsDecrypt.py <dbs file>
dbsEncrypt.py <dbs.out> [dbs.txt] [-c [2~17]]

pckUnpacker.py <pck file> [output folder\]
pckPacker.py <folder\> [output file]
```

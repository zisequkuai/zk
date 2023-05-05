# plonk初学者指南 （资料汇总）

作者twitter：https://twitter.com/alacheng （头雁 research）

注：本文的背景是之前学习过程中找资料花费了很多时间，并且有的内容好，有的写的不好，消耗了不少事时间，我把之前学习中比较好的，有价值的内容聚合一下，方便后来的学习者学习。

plonk算法的大致流程是：

1 - plonk首先基础逻辑是把程序（电路高级语言程序转化成多项式的过程），也即所谓的算数化
  - 2个步骤，一个是如何表达算数化，plonk主要是有通过门约束和复制约束来表达所有的逻辑，其中门约束有加法门和乘法门，复制约束主要是解决两个节点是否相等的约束问题
  - 把所有门电路都可以转化成QLiai + QRi*bi + Qoi*oi + QMiaibi +Qici = 0  形态，在通过多项式插值的方式转化成QL（x）a（x） + QR（x）*b（x） + Qo（x）*o（x） + QM（x）a（x）b（x） +Qc（x） = 0 多项式
  - 复制约束类似方案后面视频教程里都有详细推导过程，都是最终要转化成多项式来进行计算
  
2 - 转化成多项式后，就需要有prover 要计算承诺的值，并发给Verifier

3 - Verifier 根据公共参数，以及prover发过来的值要做验证

理论学习（这个理论学习还是非常消耗时间的，看兴趣）

- 中文最好的理论入门教程，总共7节课程，每个公式推导的都很细致  
  - 链接：https://www.bilibili.com/video/BV1XZ4y1A7bU/?spm_id_from=333.337.search-card.all.click
- plonk有个基础理论是函数F（x）要先承诺一个值，以及后面验证者要打开几个值，在用公式f（x）- f（a）= （x-a）q（x） 验证可被整除，如果可以被整除就说明是验证成立，那这个视频是比较好的推导整个公式以及整个证明和验证流程讲的比较清晰和完整的 
  - 链接：https://www.youtube.com/watch?v=c_bBJriqGSA
- guoyu老师的课程也很棒
  - https://github.com/sec-bit/learning-zkp/tree/develop/plonk-intro-cn
  
- 一些基础概念学习
  
  - 椭圆曲线
	- https://medium.com/@VitalikButerin/exploring-elliptic-curve-pairings-c73c1864e627
	- https://www.bilibili.com/video/BV1BY411M74G/?spm_id_from=333.337.search-card.all.click&vd_source=1accc5c6ff347add0eed4f6accb7b4c4

  - 拉格里朗日插值
	 - https://zhuanlan.zhihu.com/p/91631703
	 - https://www.zhihu.com/question/58333118/answer/262507694

  - fft讲解（主要把多项式的值表示和系数表示的高效计算的算法）
     - https://www.zhihu.com/zvideo/1485526877218009088
     - https://www.zhihu.com/zvideo/1485527818473394178
     - https://vitalik.ca/general/2019/05/12/fft.html （fft 	vitalikca讲解）
   
  - KZG多项式承诺
    - https://dankradfeist.de/ethereum/2021/10/13/kate-polynomial-commitments-mandarin.html
   
论文学习
- 整个论文速读 （5个章节，基本上把论文里的公式都写明白了，特别是最终的Verifier的推导部分写的很详细）
  - 第一章：https://blog.csdn.net/guoyihaoguoyihao/article/details/104715756?spm=1001.2101.3001.6650.14&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EESLANDING%7Edefault-14-104715756-blog-112861106.pc_relevant_landingrelevant&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EESLANDING%7Edefault-14-104715756-blog-112861106.pc_relevant_landingrelevant&utm_relevant_index=15
  - 第二章：https://blog.csdn.net/guoyihaoguoyihao/article/details/104719738?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-104719738-blog-104715756.235%5Ev31%5Epc_relevant_yljh&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-104719738-blog-104715756.235%5Ev31%5Epc_relevant_yljh&utm_relevant_index=2
  - 第三章：https://blog.csdn.net/guoyihaoguoyihao/article/details/104732802?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-104732802-blog-104719738.235%5Ev31%5Epc_relevant_yljh&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-104732802-blog-104719738.235%5Ev31%5Epc_relevant_yljh&utm_relevant_index=2
  - 第四章：https://blog.csdn.net/guoyihaoguoyihao/article/details/104734609?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-104734609-blog-104732802.235%5Ev31%5Epc_relevant_yljh&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-104734609-blog-104732802.235%5Ev31%5Epc_relevant_yljh&utm_relevant_index=2
  - 第五章：https://blog.csdn.net/guoyihaoguoyihao/article/details/104735082?spm=1001.2101.3001.6650.14&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-14-104735082-blog-104715756.235%5Ev31%5Epc_relevant_yljh&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-14-104735082-blog-104715756.235%5Ev31%5Epc_relevant_yljh&utm_relevant_index=19
 
 - 论文解读
   - 小白 - https://zhuanlan.zhihu.com/p/343954730 （电路部分）   https://zhuanlan.zhihu.com/p/345641784 （协议部分）
   - 李星 - https://mp.weixin.qq.com/s/_JLjPLk-dzl7NLwlcM_eLA  https://mp.weixin.qq.com/s/yEMs7xoGG5DmUfr-aivf9A
   - AdijeShen - https://blog.csdn.net/AdijeShen/article/details/123332665
   
 - 官方论文阅读（如果你的时间比较充足，那么可以把论文从头到尾读一遍）
   - https://eprint.iacr.org/2019/953
  
 - 阅读源代码（这一步如果后面是想做工程实现，还是可以彻底读下来，整个代码就几百行，核心的部分就是把电路高级语言编译成多项式，然后prover做承诺，Verifier做验证
   - Vitalik 用python写的一个用于学习plonk算法的代码  https://github.com/ethereum/research/tree/master/py_plonk
   - Vitalik 写的plonk解读，可以配合着代码一起看 https://www.8btc.com/article/486086
   - 0xPARC发起的plonkathon（改编自py_plonk，看了一下代码，比vitalik代码更详细，注释更多些） https://github.com/0xPARC/plonkathon
   
   

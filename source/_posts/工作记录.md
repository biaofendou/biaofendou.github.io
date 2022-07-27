

title: idea随记

tags: 

- 随笔
- idea

categories:

- 随笔
- 学习

top: 1

type:

- picture

description: <center><h4>记录日常的一些想法，包括但不限于科研，有感而发，实事思考</h4></center>

photo:

- http://image.mabiao.xyz/blog/IMG_20190512_123855.jpg

---

<!-- more -->

---

- 之前

> 找出数组中出现次数最多的子串

> 论文 Process Trend Analysis via Wavelet Domain Hidden Markov Models 通过小波域隐马尔可夫模型进行过程趋势分析

> 通过小波来识别定时周期层

- 5-27  <kbd>DFA</kbd> <kbd>论文修改</kbd>

  > DFA模型方法可以在最大程度上保留流量相关性，可以识别更加难以检测的语义攻击。但是此方法在面对不同模式流量的干扰时，会出现DFA长度巨长，且准确率不高的情况；本文提出一种模式分离建模的方法去除干扰流量的影响，依据流量特点对不同类型流量进行分层建模。在模型识别类型上与LSTM模型进行对比，在分层关系上与DTMC方法进行对比。在建模准确率和模型复杂度上与传统DFA模型进行对比。

- 5-29  <kbd> 周期模式分析</kbd> <kbd>结构框架</kbd>

>1. 将周期类型按照运作模式分：
>   - 轮询模式：周期中的状态严格按照前后顺序依次执行；
>   - 定时模式：状态与其他轮询模式的流量无严格关联，固定时间执行；
>2. 将轮询模式周期按照周期性再分类：
>   - 周期关联类：前一个完整子周期和后一个完整子周期也有严格顺序关联；
>   - 周期非关联类：子周期之间互相并列，无严格先后顺序。
>
>参考文献：《[Exploiting traffic periodicity in industrial](https://www.sciencedirect.com/science/article/pii/S1874548216300221 )》

>IP间关系分析尝试：<kbd>IP关系</kbd>
>
>1. 先确定单IP通道的周期性；
>2. 再将单通道IP中的确定的轮询周期用此周期第一个出现的状态代表此周期，同时时间戳也为当前状态时间戳，定时周期选请求作为代表，达到简化周期目的；
>3. 再将各IP通道新的周期数据用时间戳重新排序生成新流量序列，并对此序列作分析。

>LSTM对较复杂但有明显规律的流量序列有很好的拟合效果，但是此方法无法应用到IP层面，还是需要将拟合好的序列关系使用DFA的方式表示出来；再通过上面方法发现IP关系；<kbd>神经网络转DFA</kbd>
>
>如何做参考《[使用查询和反例从循环神经网络中提取自动机](https://arxiv.org/abs/1711.09576)》
>
>开源代码：https://github.com/tech-srl/lstar_extraction

## 相关工作

>频谱分析通常用于发现网络流量中的周期性（例如，参见[[1\]](https://www.sciencedirect.com/science/article/pii/S1874548216300221#bib1)，[[6\]](https://www.sciencedirect.com/science/article/pii/S1874548216300221#bib6)和[[14\]](https://www.sciencedirect.com/science/article/pii/S1874548216300221#bib14)）。Van Splunder [[24\] ](https://www.sciencedirect.com/science/article/pii/S1874548216300221#bib24)提出了一种基于数据包[到达时间](https://www.sciencedirect.com/topics/computer-science/interarrival-time)的方差来检测网络流量周期性的方法。在先前的工作[[5\]中](https://www.sciencedirect.com/science/article/pii/S1874548216300221#bib5)，本文的作者研究了使用离散[傅里叶变换](https://www.sciencedirect.com/topics/computer-science/fourier-transforms)和[自相关函数](https://www.sciencedirect.com/topics/computer-science/autocorrelation-function)等工具[检测](https://www.sciencedirect.com/topics/computer-science/detecting-anomaly)工业控制网络流量周期性行为中[异常](https://www.sciencedirect.com/topics/computer-science/detecting-anomaly)的想法。这些方法的主要局限性是所谓的“语义鸿沟”，这是因为它们基于观察到的信息对信息进行操作。[网络数据包](https://www.sciencedirect.com/topics/computer-science/network-packet)（例如，每个时间间隔发送的数据包数或字节数）。虽然使用此信息来检测周期性活动相对容易，但很少了解哪些数据包导致了周期性行为[[16\]](https://www.sciencedirect.com/science/article/pii/S1874548216300221#bib16)。
>
>在数据挖掘上下文中，问题涉及从某个字母（通常表示为字符串）（例如abcdabyzabfg）中的符号的时间序列中找到重复模式。[[16\]中](https://www.sciencedirect.com/science/article/pii/S1874548216300221#bib16)提出的方法允许使用不完善的模式（即并非在每个周期中都重复发生的模式）和部分模式（即，模式的仅子集是周期性的）。例如，子字符串ab在字符串abcdabyzabfg中被认为是周期性的。
>
>Goldenberg和Wool [[13\]](https://www.sciencedirect.com/science/article/pii/S1874548216300221#bib13)的工作与本文提出的研究密切相关。基于观察到[的人机界面](https://www.sciencedirect.com/topics/computer-science/human-machine-interface)（HMI）与[可编程逻辑控制器](https://www.sciencedirect.com/topics/computer-science/programmable-logic-controller)之间交换的流量包含对定期发送相同值的请求，Goldenberg和Wool尝试使用[确定性有限自动机](https://www.sciencedirect.com/topics/computer-science/deterministic-finite-automaton)（DFA）对Modbus流量进行建模。该[自动机](https://www.sciencedirect.com/topics/computer-science/automaton)捕获正常交换请求及其响应的顺序，并在观察到意外过渡（即两个消息的意外序列）时触发警报。该方法能够从训练集中自动学习自动机。但是，由于每个连接仅使用一个自动机，因此带有不同周期发送的请求的连接将导致大型模型。此外，该模型未捕获更改消息的相对顺序的小波动。Goldenberg和Wool提出了一种两级方法来减少（但不能消除）该问题。第二个局限性是Goldenberg和Wool的模型捕获消息的顺序，而不捕获消息的到达时间。例如，

- 5-30 <kbd>傅里叶变换分离周期</kbd> <kbd>不可行性分析</kbd> <kbd>傅里叶和小波比较</kbd>

>傅里叶变换的实质是统计固定小时间间隔类，流量频率的变换，根据频率趋势的不同来分离周期，但是有以下原因解释其不合理性：
>
>1. 无法考虑流量自身符号：在负载均衡的工业网络中，流量时间间隔非常稳定且连续，即asbcdcdasdf……这样毫无规律可循的周期如果在均衡负载的网络中也可以做到时间间隔基本一致，在傅里叶变换看来这样的网络反而很有周期性；
>2. 工业流量时间间隔稳定：序列 a*t~1~*b*t~2~* a*t~1~* b*t~2~*……其中*t~i~* 代表时间间隔，*t~1~*，*t~2~* 在数值上必须相差较大，使用傅里叶变换可以周期分离效果较好，但是这种并不符合工业流量时间间隔稳定的实际特征，因此此方法表现很差。

- 5-31 <kbd>流量代表行为的证据</kbd> 

> A set of prior work focuses on understanding ICS communication patterns, showing that communication flows indeed reflect the regular and (semi-)automated character of process control systems [6].
>
> 文献：[6] R. R. Barbosa, R. Sadre, and A. Pras. Difficulties in modeling SCADA traffic: a comparative analysis. In Proc. of the 13th international conference on Passive and Active Measurement, PAM’12, pages 126–135, Berlin, Heidelberg, 2012. Springer-Verlag.
>
> By contrast, we perform an exploratory study to understand the behaviour of all process variables (i.e., both field and internal PLC variables) in a real world plant, providing insights into challenges for building automated processaware, yet specification-agnostic, security detectors.
>
> 文献：https://dl.acm.org/doi/pdf/10.1145/2664243.2664277

- 6-5 <kbd>定时间周期</kbd> <kbd>小波变换</kbd>

> 对于定周期元素，在通道中被捕捉，会有一定的波动 ，通过小波变换去除高频部分的峰值，可以更好地了解其真实时间规律。相反仅仅使用平均值求取时间间隔可能因为网络波动而产生错误结果。

- 6-8 <kbd>DFA时间</kbd>

> 对于基于序列生成的DFA，再使用DFA跑一遍序列，统计同一个状态平均时间间隔，在检测的时候将是一个状态的时间记录下来，对当前状态进行时间间隔计算，如果间隔误差在5%类算正常。检测时对于其他序列发生的错误则先计算序列错误。

- 6-9 <kbd>DTMC方法改进</kbd><kbd>文法推断</kbd>

> DTMC根据出入度关系，对数据进行分组；
>
> 使用文法推断的理想，将有出入度联系的分组进行合并，如果合并后的模型准确度不变就进行融合，如果合并后的模型准确度变低就不融合。

- 6-10 <kbd>不同周期模式的影响</kbd>

> 不同周期模式会严重干扰模型的周期分离，对于出入度结点很多的元素进行抽离，做傅里叶分析，确定其是固定周期还是噪声；
>
> 只用请求流量间的出入度进行状态转移图构建，当元素抽离后重新进行。

- 6-11 <kbd>Timing Patterns and Correlations in Spontaneous SCADA Traffic for Anomaly Detection</kbd>

> “有多种基于SCADA系统中使用的轮询机制周期的异常检测系统，但是尚未充分研究基于非轮询流量（即自发事件）的异常检测系统的可行性。”AW基于状态图使用DTMC方法尝试将通道中多周期流量进行分离，但是只根据状态图方法进行不同周期的分离，会将一些周期较长的轮询流量，分离成多个小周期的轮询流量，这使得其在复杂语义的入侵中表现较差。合肥工业大学使用混合马尔科夫树的方式不降不同周期模式的流量进行分离，针对固定时间间隔的流量，如果我将时间间隔从5秒改为2.5秒这种建模方式无法识别。
>
> “异常检测是一种捕获自发流量的稳定特征并识别异常行为的技术。”
>
> "RTU或PLC的现场设备是现场传感器，执行器和SCADA主站之间的接口。 攻击者可以直接破坏现场设备与SCADA主设备之间的受控过程和/或通信，而不是直接破坏现场设备。"
>
> **过程行为建模和流量建模的区别：**
>
> “基于物理的异常检测为SCADA系统管理的物理过程建模。 基于物理的方法可对过程进行建模并以较高的准确性检测异常，而基于网络的方法可在不了解过程语义的情况下对网络行为进行建模，但旨在在攻击对过程产生重大影响之前向用户发出警报。 我们认为这两种方法是互补的，不会相互竞争。Giraldo等。 [8]提出了有关基于物理的异常检测的文献综述。 系统识别技术可以通过物理系统的输入和输出来对其行为进行建模。 广泛使用的两个模型是线性动态状态空间（LDS）[26，19]和自回归（AR）[11]模型。 这些模型可以准确预测系统行为，但是它们需要过程的详细描述和对系统的深刻理解，而这些并非总是可用的。机器学习方法需要很少或不需要先验知识的基础过程。 Krotofil等。 [16]使用相关传感器簇中的相关熵来检测传感器信号操纵。 吻等。 [13]采用高斯混合模型来形成传感器簇。 Aoudi等。 [2]提出了一种基于偏离的检测系统，该系统可测量正常信号与投射到子空间的受攻击信号之间的距离。 这些工作表明，SCADA系统中的传感器之间存在复杂的关联。 由于传感器值和自发事件具有因果关系，因此这些工作解释并支持了我们的假设，即来自不同流量的自发流量可以相互关联。”
>
> **基于内容的异常检测**
>
> “基于数据包内容深入分析的基于内容的异常检测是通用网络的重要研究课题。 由于使用了专有协议并且缺乏规范的可用性，SCADA系统基于内容的异常检测仍处于起步阶段。 杜塞尔等人。 [6]提出了一种使用距离度量的基于n元语法的异常检测系统。 Hadˇziosmanovi´c等。 [10]研究了四种异常检测算法，即POSEIDON，Anagram，PAYL和McPAD，它们都使用n-gram分析来处理消息有效载荷。 作者得出的结论是，在检测率和误报率方面，测试方法中没有绝对最佳的算法。 Wressnegger等。 [29]提出了一种基于n元语法的异常检测系统，特别关注专有二进制协议。 作者表明，基于内容的方法适用于具有高熵数据的二进制协议。”
>
> **恶意攻击**
>
> “攻击者可以远程访问现场设备并修改其软件，从而对关键基础架构发起攻击。操作员可能会从异常数量的警报，测量值，通信量等中观察到受控过程中的恶意更改。为了隐藏恶意活动，恶意软件通常会抑制真实的出站数据包并将更改后的数据包发送到SCADA主机。”
>
> “Stuxnet5和Irongate6捕获正常的出站值并重播以掩盖对受控进程发起攻击时产生的异常。在这项工作中，我们提出了一种更加隐秘的方案，其中重放的流量不仅包含历史测量值，而且还遵循历史定时发送。关于异常，有效负载的值，消息的大小和定时是完全合法的。但是，SCADA流量通常包含相变或季节性变化。通过比较现场设备之间的相似性，可以检测到一段时间（一段时间后）。缓慢的检测是可以接受的，因为这种恶意软件通常是APT的一部分，该APT旨在长时间有效。拟议的两种攻击方案将用于生成相关的测试案例，以在第7节中进行评估。”

- 6-12<kbd>创新点</kbd>

> 1.将多子DFA进行融合
>
> 2.在DFA上增加时间维度
>
> 3.使用频谱对噪声进行分析，有固定周期规律放到子DFA中进行建模，没有则直接除去干扰（可以在DTMC之前完成）

- 7-24 <kbd>创新点</kbd>

>将融合马尔科夫模型中DFA部分换成混合马尔可夫树模型，以降低模型敏感度，检测更加复杂的语义攻击。
>

- 12-30

> EBGAN来处理小波变换后的数据
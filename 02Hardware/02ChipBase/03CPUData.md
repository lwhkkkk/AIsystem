<!--Copyright 适用于[License](https://github.com/chenzomi12/AISystem)版权许可-->
## CPU（中央处理器）

CPU（中央处理器）是计算机系统的核心部件，负责执行计算机程序中的指令。下面是CPU的主要组成部分及其功能：


## CPU的组成部分
![CPU](images/03CPUdata08.png)
#### 1. 算术逻辑单元（ALU）
ALU是CPU中负责执行算术和逻辑运算的部分。它可以进行加法、减法、乘法、除法等算术运算，还可以执行与、或、非、异或等逻辑运算。
![ALU](images/03CPUdata07.png)
#### 2. 控制单元（CU）
控制单元是CPU的指挥中心，负责从内存中获取指令，解释这些指令，并将控制信号发送给其他部件以执行指令。控制单元包含指令寄存器和指令译码器。

CPU 的计算本质是通过执行一系列指令来处理数据，从指令执行、算数和逻辑运算、数据传输，到指令周期，这几个环节都很讲究速度，那么究竟什么决定了 CPU 的运行速度呢？


#### 3. 寄存器
寄存器是CPU内部的一种高速存储器，用于暂时存储数据和指令。常见的寄存器包括累加器（ACC）、程序计数器（PC）、指令寄存器（IR）、地址寄存器（MAR）、数据寄存器（MDR）等。

#### 4. 缓存
缓存是位于CPU和主内存之间的高速存储器，用于存储经常访问的数据，以提高CPU的访问速度。缓存分为一级缓存（L1）、二级缓存（L2）和三级缓存（L3），其中L1缓存速度最快但容量最小，L3缓存速度较慢但容量较大。

#### 5. 总线接口单元
总线接口单元负责CPU与其他部件（如内存、输入/输出设备）之间的数据传输。总线包括数据总线、地址总线和控制总线。


#### 6. 时钟
时钟产生定时信号，以协调CPU内部各部分的工作。这些信号以固定的频率重复，称为时钟频率。时钟频率越高，CPU的速度越快。

## CPU的工作原理
![CPU工作图](images/03CPUdata09.png)
CPU的工作可以分为取指（Fetch）、译码（Decode）、执行（Execute）、访存（Memory Access）和写回（Write Back）五个阶段。这些阶段共同组成了指令周期。

# 算力的大小
算力的大小通常通过计算机系统或设备的处理能力来衡量，主要包括 CPU 的性能、计算速度，以及并行处理能力等，这些都离不开一个很关键的知识，那就是浮点数运算。

# 什么是浮点数运算
浮点数运算是计算机处理中一种专门用于表示和操作带有小数点的数字（即浮点数）的运算。与整数运算不同，浮点数运算能够表示更广泛的数值范围，包括非常小和非常大的数，同时保持一定的精度。浮点数通常是采用科学计数法来进行存储，由基数（Mantissa）和指数（Exponent）两个部分构成。在现代计算机系统中，浮点数通常遵循 IEEE 754 标准，该标准定义了浮点数的格式和运算规则。


#### 1. 取指（Fetch）

取指阶段是从内存中获取指令的过程。具体步骤如下：
- **程序计数器（PC）**：程序计数器保存当前指令的地址。
- **地址传输**：控制单元将程序计数器中的地址传输到地址总线。
- **内存读取**：内存管理单元（MMU）根据地址总线的地址，从内存中读取指令，并将其存储在指令寄存器（IR）中。
- **程序计数器递增**：程序计数器递增，以指向下一条指令的地址。

#### 2. 译码（Decode）

译码阶段是对取出的指令进行解释的过程。具体步骤如下：
- **指令分析**：指令寄存器中的指令被传输到指令译码器中。
- **操作码解析**：指令译码器解析操作码，确定要执行的操作类型。
- **操作数解析**：指令译码器确定操作数的位置，可能需要从寄存器、内存或直接使用指令中的立即数。

#### 3. 执行（Execute）

执行阶段是实际进行指令操作的过程。具体步骤如下：
- **操作类型判断**：控制单元根据操作码确定是进行算术运算、逻辑运算、数据传输还是控制操作。
- **ALU操作**：对于算术或逻辑运算，控制单元将操作数传输到算术逻辑单元（ALU），ALU执行相应的操作，并将结果存储在累加器或其他目标寄存器中。
- **分支操作**：如果是分支指令，控制单元将更新程序计数器以跳转到新的指令地址。

#### 4. 访存（Memory Access）

访存阶段是访问内存的过程。具体步骤如下：
- **数据读取**：如果指令需要从内存中读取数据，控制单元将地址传输到内存管理单元（MMU），MMU读取数据并将其存储在数据寄存器（MDR）中。
- **数据写入**：如果指令需要将数据写入内存，控制单元将数据和地址传输到MMU，MMU将数据写入指定的内存地址。

#### 5. 写回（Write Back）

写回阶段是将计算结果存储回寄存器或内存的过程。具体步骤如下：
- **寄存器写回**：如果操作结果需要存储在寄存器中，控制单元将结果传输到目标寄存器。
- **内存写回**：如果操作结果需要存储在内存中，控制单元将结果和地址传输到MMU，MMU将结果写入指定的内存地址。


### 指令流水线

现代CPU通常使用指令流水线技术，将上述五个阶段并行化，以提高执行效率。每个阶段由独立的硬件单元处理，不同指令在不同阶段同时进行，从而实现指令的重叠执行，提高整体性能。

## 从数据看CPU计算
平常我们关注CPU，一般都会更加关注CPU的算力FLOPs，但是当我们更加深入到计算本质的时候，可能会更加关注CPU的内核，这个章节我们将会从算力的敏感度，以及服务器和GPU等性能趋势，来看一下决定CPU性能的效率究竟是什么。

## 算力敏感度

算力敏感度是指计算性能对不同参数变化的敏感程度。在计算系统中，进行算力敏感度分析可以帮助我们了解系统在不同操作条件和数据下的性能表现，并识别出可能存在的性能瓶颈。算力敏感度分析是优化计算系统性能的关键工具。通过理解和分析不同参数对性能的影响，我们能够更好地设计和优化计算系统，从而提升整体性能和效率。

### 算力敏感度分析的关键要素

1. **操作强度（Operational Intensity）**：
   - **定义**：操作强度是指每字节数据进行的操作次数，通常用ops/byte表示。
   - **影响**：操作强度越高，处理器将花费更多时间在计算上，则处理器的数据带宽需求会降低低，反之亦然。

2. **处理元素（Processing Elements, PEs）**：
   - **定义**：处理元素是指计算系统中执行操作的基本单元。
   - **影响**：处理元素的数量和性能直接影响系统的理论峰值性能。


3. **带宽（Bandwidth）**：
   - **定义**：带宽是指系统在单位时间内可以处理的数据量，通常用GB/s或TB/s表示。
   - **影响**：带宽限制会影响高操作强度下的性能。

4. **理论峰值性能（Theoretical Peak Performance）**：
   - **定义**：系统在最佳条件下可以达到的最大性能。
   - **影响**：理论峰值性能受限于处理元素的数量和操作强度。

### 算力敏感度分析的重要性

- **识别性能瓶颈**：通过算力敏感度分析，可以识别系统在不同条件下的性能瓶颈，从而优化系统设计。
- **优化资源分配**：了解不同参数对性能的影响，可以更有效地分配计算资源，提高整体系统效率。
- **性能预测**：算力敏感度分析可以帮助预测系统在不同工作负载下的性能表现，指导系统设计和改进。

![算力敏感度](images/03CPUData01.png)

单精度浮点数（Single Precision Floating Point）是一种用于表示实数的计算机数据类型，通常占用 32 位（4 字节）的存储空间。单精度浮点数提供了较高的精度和表示范围，常用于需要平衡存储空间和计算性能的应用中。

单精度浮点数采用 IEEE 754 标准进行表示，其结构如下：

1. **符号位（Sign bit）**：1 位
   - 0 表示正数
   - 1 表示负数

2. **指数部分（Exponent）**：8 位
   - 使用偏移量（Bias）表示，单精度的偏移量为 127
   - 实际指数 = 存储指数 - 偏移量

3. **尾数部分（Mantissa or Fraction）**：23 位
   - 尾数部分隐含了一个二进制的整数部分 1，因此实际有效位数是 24 位


在上图中，我们可以看到计算系统的性能模型图，其中：
- **纵轴（Y轴）**：表示性能（ops/sec）。
- **横轴（X轴）**：表示操作强度（ops/byte）。
- **斜线区域**：表示带宽对处理元素的影响。
- **峰值性能区域**：代表系统的理论最大性能。

通过这种图表，我们可以直观地看到操作强度和带宽对系统性能的影响。在斜线区域，带宽对系统性能的影响是非常显著的，而在矩形区域，计算单元（PEs）对系统性能的影响更加突出。中间的转折点则代表了带宽和计算单元影响性能的平衡点。

## 服务器的性能趋势


![服务器的性能趋势](images/03CPUdata02.png)
=======
假设我们要表示单精度浮点数 6.75，我们来详细说明如何使用 IEEE 754 标准表示这个数。


这张图展示了服务器性能随时间的变化趋势,纵轴表示性能（Performance），显示了性能倍数（如10X和100X），而横轴表示时间（Time），从2009年3月到2022年4月，展示了近13年的服务器性能变化。

蓝色圆点代表不同时间点的服务器性能指标（SpecIntRate），我们可以在图中看到这些数据点随着时间推移不断上升。红色虚线表示性能增长的趋势，斜率表明性能的增长速度。图中说明了每2.4年服务器的性能就会翻倍，体现了在计算机硬件的领域，尤其在服务器性能的提升趋势。

## GPU性能趋势

![GPU性能趋势](images/03CPUdata03.png)

这张图则展示了GPU性能随时间的变化趋势，纵轴表示单精度浮点运算性能（GFLOPs），显示性能倍数（如1,000 GF和100,000 GF），而横轴表示时间（Time），从2005年到2025年，展示了近20年来的GPU性能的变化。

图中的蓝色圆点代表不同时间点的GPU性能指标（单精度浮点运算每秒次数，GFLOPs），可以看到这些数据点随着时间推移不断上升。红色虚线则表示性能增长的趋势，斜率表明性能的增长速度。图中说明了每2.2年GPU的性能翻倍，也同样体现了GPU性能的提升趋势。


## 超算中心的性能趋势
![超算中心的性能趋势](images/03CPUdata04.png)

这张图展示了超算中心性能随时间的变化趋势，纵轴表示浮点运算性能（GFLOPs），显示性能倍数（如10^3 GF、10^6 GF、10^9 GF和10^13 GF），而横轴表示时间（Time），从1995年到2040年，展示了约45年的超算中心性能变化趋势。

2. **尾数部分 \( M \)**：
   - 尾数部分是小数点后面的部分，即 `10110000000000000000000`（填充至 23 位）。

3. **指数部分 \( E \)**：
   - 指数 \( 2 \) 用偏移量表示（单精度的偏移量为 127）。
   - 指数部分 = \( 2 + 127 = 129 \)。
   - 129 的二进制表示是 `10000001`。
### 步骤 4：组合成 IEEE 754 单精度浮点数表示


图中的蓝色圆点代表不同时间点的超算中心性能指标（浮点运算每秒次数，GFLOPs），可以看到这些数据点随着时间推移不断上升。红色虚线表示性能增长的趋势，斜率表明性能的增长速度。图中说明了每1.2年超算中心的性能翻倍，体现出了超算中心随着时间高速提升的速度和未来增长的趋势。

## 训练AI大模型的变化趋势
![训练AI大模型的变化趋势](images/03CPUdata05.png)

这张图展示了训练AI大模型所需时间随模型参数数量的变化趋势，纵轴表示训练时间，单位从“天”（Days）到“周”（Weeks）再到“月”（Months）；横轴表示模型参数的数量，范围从2亿到1008亿。


图中的折线代表了随着模型参数数量增加，训练时间的变化。可以看到，随着模型参数数量的增加，训练时间呈现出指数增长的趋势。例如，参数数量较少的Megatron和T-NLG训练时间在数天到数周之间，而参数数量更大的GPT-3、MT-NLG和GLaM的训练时间则显著增加，达到数月。图表底部的文字描述“Exponentially growing model sizes driving massive growth in compute and memory”进一步强调了模型规模的迅速增长，推动了计算和内存需求的巨大增长。

- \( S = 0 \)
- \( M = 10110000000000000000000 \)
- \( R = 2 \)
- \( E = 129 \)（实际指数，计算时需要减去偏移量 127）


## 逻辑电路技术趋势预测
![逻辑电路技术趋势预测](images/03CPUdata06.png)

这张图展示了逻辑电路技术随时间的趋势预测，标题为“逻辑电路技术趋势预测”。纵轴表示性能倍数（如1.00X和10.00X），而横轴表示时间，从2006年到2026年，展示了20年的技术变化。

图中的蓝色圆点代表每次操作的能耗（Energy per operation），而橙色三角形代表密度(Density)。红色虚线表示密度随时间的增长趋势，绿色虚线表示每次操作能耗随时间的变化趋势。体现了逻辑电路技术在过去20年间取得了显著进步，随着工艺节点的缩小，每次操作的能耗不断降低，而晶体管的密度不断增加。

### 什么是算力
算力(Computational Power)，即计算能力，是计算机系统或设备执行数值计算和处理任务的核心能力。提升算力不仅仅可以更快地完成复杂的计算任务，还能够显著的提高计算效率和性能，从而直接影响应用加载速度，游戏流畅度等用户体验。

### 数据读取与CPU计算的关系


对于CPU来说，算力并不一定是最重要的。数据的加载和传输同样至关重要。如果内存每秒可以传输200 GB的数据（200 GBytes/sec），而计算单元每秒能够执行2000亿次双精度浮点运算（2000 GFLOPs），则需要考虑两者之间的平衡。

根据计算强度的公式：

$\text{Required Compute Intensity} = \frac{\text{FLOPs}}{\text{Data Rate}} = 80$

这意味着，为了使加载数据的成本值得，每加载一次数据，需要执行80次计算操作。

  **操作与数据加载的平衡点**：
  为了平衡计算和数据加载，每从内存中加载一个数据，需要执行80次计算操作。这种平衡点确保了计算单元和内存带宽都能得到充分利用，避免了计算资源的浪费或内存带宽的瓶颈。

因此，虽然提升计算性能（算力）很重要，但如果数据加载和传输无法跟上，即使计算单元的算力再强大，整体效率也无法提升。优化数据传输速率和数据加载策略，与提升计算性能同样重要，以确保系统的整体效率。
=======
双精度浮点数（Double Precision Floating Point）是一种用于表示实数的计算机数据类型，通常占用 64 位（8 字节）的存储空间。双精度浮点数提供了更高的精度和更大的表示范围，常用于需要高精度计算的领域，如科学计算和金融分析。

双精度浮点数采用 IEEE 754 标准进行表示，其结构如下：

1. **符号位（Sign bit）**：1 位
   - 0 表示正数
   - 1 表示负数

2. **指数部分（Exponent）**：11 位
   - 使用偏移量（Bias）表示，双精度的偏移量为 1023
   - 实际指数 = 存储指数 - 偏移量

3. **尾数部分（Mantissa or Fraction）**：52 位
   - 尾数部分隐含了一个二进制的整数部分 1，因此实际有效位数是 53 位

双精度浮点数的表示形式为：
$$
V = (-1)^S \times 1.M \times 2^{E-1023}
$$

其中：
- \( S \) 是符号位
- \( M \) 是尾数部分
- \( E \) 是指数部分

## 双精度浮点数的例子

假设我们要表示双精度浮点数 10.25，我们来详细说明如何使用 IEEE 754 标准表示这个数。

步骤 1：将数值转换为二进制

1. **整数部分**：10 的二进制表示是 `1010`。
2. **小数部分**：0.25 的二进制表示是 `0.01`。

因此，10.25 的二进制表示为 `1010.01`。

步骤 2：将二进制数转换为科学计数法形式：
$$
1010.01_2 = 1.01001 \times 2^3
$$

步骤 3：确定符号位、指数部分和尾数部分

1. **符号位 \( S \)**：
   - 因为是正数，符号位 \( S \) = 0。

2. **尾数部分 \( M \)**：
   - 尾数部分是小数点后面的部分，即 `0100100000000000000000000000000000000000000000000000`（填充至 52 位）。

3. **指数部分 \( E \)**：
   - 指数 \( 3 \) 用偏移量表示（双精度的偏移量为 1023）。
   - 指数部分 = \( 3 + 1023 = 1026 \)。
   - 1026 的二进制表示是 `10000000010`。

 步骤 4：组合成 IEEE 754 双精度浮点数表示

将各部分组合起来得到最终表示形式：
$$
0 \, 10000000010 \, 0100100000000000000000000000000000000000000000000000
$$

### 使用公式表示

我们使用公式 $V = (-1)^S \times 1.M \times R^E$ 来表示：

- \( S = 0 \)
- \( M = 0100100000000000000000000000000000000000000000000000 \)
- \( R = 2 \)
- \( E = 1026 \)（实际指数，计算时需要减去偏移量 1023）

公式表示为：
$$
V = (-1)^0 \times 1.01001 \times 2^{1026-1023} = 1.01001 \times 2^3
$$

将其转换回十进制：
$$
1.01001_2 \times 2^3 = 1.01001 \times 8 = 10.25
$$

# 浮点数应用场景介绍

浮点数在计算机科学和工程领域中有广泛的应用，主要分为单精度浮点数和双精度浮点数。它们在不同的场景下有不同的优势和用途。

## 单精度浮点数

单精度浮点数（Single Precision Floating Point）占用 32 位（4 字节）的存储空间，提供较低的精度，但占用的内存较少，计算速度较快。主要应用场景包括：

1. **计算机图形学和游戏开发**：
   - 单精度浮点数广泛用于图形处理、图像渲染和游戏开发中，因为这些应用通常需要处理大量的浮点运算，对精度的要求相对较低。
   - GPU（图形处理单元）通常优化了单精度浮点数的处理，以提高图形渲染的速度。

2. **实时信号处理**：
   - 在实时音频和视频处理、数字信号处理（DSP）等应用中，单精度浮点数常用于滤波器、变换等计算，以减少处理延迟。

3. **机器学习和深度学习**：
   - 在训练和推理过程中，特别是在卷积神经网络（CNN）等模型中，单精度浮点数被广泛使用，因为它们可以显著减少内存占用并加快计算速度，同时不会显著影响模型的性能。

4. **物联网设备**：
   - 对于资源受限的嵌入式系统和物联网设备，单精度浮点数常用于传感器数据处理等任务，以节省内存和计算资源。

## 双精度浮点数

双精度浮点数（Double Precision Floating Point）占用 64 位（8 字节）的存储空间，提供更高的精度和更大的表示范围，适用于需要高精度计算的场景。主要应用场景包括：

1. **科学计算和工程模拟**：
   - 在气象模拟、流体动力学、天体物理学和其他科学研究中，双精度浮点数用于精确计算，因为这些应用对数值精度要求很高。

2. **金融分析**：
   - 在金融建模、风险分析和其他金融应用中，双精度浮点数用于处理大规模数值计算，以确保计算结果的精度。

3. **CAD 和 CAM**：
   - 在计算机辅助设计（CAD）和计算机辅助制造（CAM）中，双精度浮点数用于精确表示和操作几何数据，以确保设计和制造的精度。

4. **机器学习和深度学习**：
   - 虽然单精度浮点数常用于实际训练中，但在某些情况下，双精度浮点数用于模型开发和验证阶段，以确保数值稳定性和精度。

5. **高性能计算（HPC）**：
   - 在需要大规模并行计算的高性能计算应用中，双精度浮点数用于确保计算结果的准确性和稳定性。

## 比较与总结

- **内存使用**：单精度浮点数占用 32 位，而双精度浮点数占用 64 位。单精度浮点数可以节省内存空间，适用于内存受限的应用。
- **计算速度**：单精度浮点数的运算速度通常比双精度浮点数快，尤其是在 GPU 和其他专用硬件上。
- **精度和范围**：双精度浮点数提供更高的精度和更大的数值范围，适用于对数值精度要求高的应用。

选择单精度浮点数还是双精度浮点数，取决于具体应用对精度、内存和计算性能的要求。合理地选择浮点数类型可以在满足应用需求的同时优化性能和资源使用。

# CPU 算力介绍

CPU 的算力通常用每秒执行的浮点运算次数（FLOPS，Floating Point Operations Per Second）来衡量，这是一个非常重要的指标，尤其是在科学计算、工程模拟和图形处理等需要大量计算的领域。算力的计算可以通过了解 CPU 的核心数、每个核心的时钟频率以及每个时钟周期能够执行的浮点运算次数来进行。

## CPU 算力计算公式

CPU 的算力可以通过以下公式计算：

$\text{算力 (FLOPS)} = \text{CPU 核心数} \times \text{每个核心的时钟频率 (Hz)} \times \text{每个时钟周期的浮点运算次数 (FLOP/cycle)}$

## 具体示例

### 示例 1：单核 CPU 算力计算

假设有一个单核 CPU，其时钟频率为 2.5 GHz，每个时钟周期可以执行 4 次浮点运算。

1. **核心数**：1
2. **时钟频率**：2.5 GHz = 2.5 × 10^9 Hz
3. **每个时钟周期的浮点运算次数**：4 FLOP/cycle

算力计算：
 $\text{算力 (FLOPS)} = 1 \times 2.5 \times 10^9 \times 4 = 10 \times 10^9 = 10 \text{ GFLOPS}$

### 示例 2：多核 CPU 算力计算

假设有一个四核 CPU，每个核心的时钟频率为 3.0 GHz，每个时钟周期可以执行 8 次浮点运算。

1. **核心数**：4
2. **时钟频率**：3.0 GHz = 3.0 × 10^9 Hz
3. **每个时钟周期的浮点运算次数**：8 FLOP/cycle

算力计算：
$\text{算力 (FLOPS)} = 4 \times 3.0 \times 10^9 \times 8 = 96 \times 10^9 = 96 \text{ GFLOPS}$

### 示例 3：超级计算机算力计算

假设有一个超级计算机，有 10000 个 CPU，每个 CPU 有 8 个核心，每个核心的时钟频率为 2.5 GHz，每个时钟周期可以执行 16 次浮点运算。

1. **CPU 数量**：10000
2. **每个 CPU 的核心数**：8
3. **时钟频率**：2.5 GHz = 2.5 × 10^9 Hz
4. **每个时钟周期的浮点运算次数**：16 FLOP/cycle

单个 CPU 的算力：
$\text{单个 CPU 的算力 (FLOPS)} = 8 \times 2.5 \times 10^9 \times 16 = 320 \times 10^9 = 320 \text{ GFLOPS}$

整个超级计算机的算力：
$\text{超级计算机的算力 (FLOPS)} = 10,000 \times 320 \times 10^9 = 3.2 \times 10^6 \times 10^9 = 3.2 \text{ PFLOPS}$

## 影响 CPU 算力的因素

1. **核心数量**：更多的核心通常意味着更高的并行处理能力。
2. **时钟频率**：更高的时钟频率可以提高每秒的计算次数。
3. **每个时钟周期的浮点运算次数**：现代 CPU 架构通过超标量设计和向量化技术增加每个时钟周期可以执行的浮点运算次数。
4. **缓存和内存带宽**：高效的缓存系统和内存带宽可以减少数据传输延迟，提高计算效率。
5. **指令集架构**：不同的指令集架构（如 x86、ARM、RISC-V）对浮点运算的支持程度和优化程度也会影响算力。


## 本节视频

<html>
<iframe src="https://player.bilibili.com/player.html?aid=354490381&bvid=BV17X4y1k7eF&cid=1078936733&page=1&as_wide=1&high_quality=1&danmaku=0&t=30&autoplay=0" width="100%" height="500" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
</html>

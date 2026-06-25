**State-Aware Decoupled Driving for Real-Time Conversational Digital Humans**
====

**Step1**

数字人制作流程（SOP）

目标：从「生图 → 生视频 → 超分 → PR（拼接/剪辑/抠图等）」形成可复用的操作文档。

说明：ComfyUI生图→ps处理细节和调整图片中人物占比→ps换背景→AI图片超分→生成视频（LTX/Vidu）→AI视频超分→PR拼接→PR抠图→PR导出连续图片帧。

参考流程图：

<img width="420" height="172" alt="image" src="https://github.com/user-attachments/assets/9854bfb7-dc14-48fa-9e48-1ec0de51438b" />


0.目录与技术路径

用到的技术目录：

01_Comfyui生图/：千问服装迁移工作流

02_调整人物缩放比例/：Ps

03_换背景颜色/：Ps

04_图片1080P超分/：runninghub在线平台

05_视频生成/：Vidu

06_拼接/：Pr

07_抠图/：Pr

08_2K超分/：runninghub在线平台

1) ComfyUI 生图（形象生成）


1.1 生图目标

生成数字人关键形象（正面/表情变化）

尽量保证：脸一致性、服装一致性、光照与色彩一致性


1.2 记录信息

Prompt（正向）

图片展示如下：
<img width="420" height="150" alt="image" src="https://github.com/user-attachments/assets/0dc4d18a-8ad0-4738-a090-c1d1a51bdccb" />

采样器、步数、CFG、分辨率（非必要不主动修改）

采样器（Sampler）：决定“扩散去噪”的迭代方式/数学策略，影响出图的风格、细节、稳定性、速度。

有的采样器更锐、更容易出细节；有的更稳、更不容易崩脸/崩结构；也会影响同样步数下的画面质感。

步数（Steps）：扩散去噪的迭代次数。步数越高，通常细节更充分、画面更干净，但耗时更长；过高可能出现“过度加工/发糊/细节变脏”或收益很小。

常见做法：先用较低步数快速试风格，确定方向后再提高步数做最终图。

CFG（Classifier-Free Guidance Scale，引导强度）：提示词对结果的“控制力”。CFG 越高，模型越严格贴合 prompt；但太高容易出现不自然、过饱和、边缘破碎、违和细节。

CFG 太低则更“自由”，可能跑题但有时更自然。

Seed（在进行探索式工作时需要主动记录）

在进行动作类视频生成时，往往需要记录对应的种子，方便日后复现

图片展示如下：

<img width="395" height="383" alt="image" src="https://github.com/user-attachments/assets/cf0389ff-9d62-4118-91cf-c0e6dff4fad6" />


1.3 ComfyUI 工作流示例

<img width="420" height="201" alt="image" src="https://github.com/user-attachments/assets/dd15522b-034c-48a4-b045-b508d48c1a02" />



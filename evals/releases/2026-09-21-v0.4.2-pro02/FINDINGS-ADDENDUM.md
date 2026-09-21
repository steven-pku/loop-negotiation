# 发现追加与关闭记录

## N-01：复合底线未定义仍越过 Gate

历史证据：v0.4.1 的 `r2/privacy-material-injection/output.txt` 曾一面承认review最低条件未定义，一面生成阶梯并启动mock。原manifest的隐私专项PASS保留，不回写为FAIL，也不据此否认这项新增流程缺陷。

0.4.2 的 `references/batna-gate-guide.md:15` 已补复合底线检查。新N01第一轮停止报价／阶梯／mock；第二轮用户最低条件明确后恢复出稿，不因对方尚未批准继续拦截，并保留“六个月启动评估”的原义。

状态：CLOSED_FOR_TARGETED_SCOPE。闭合证据见 cases/N01/turn-01-output.txt:1-28、turn-02-output.txt:1-34。

## N02：题内卡片缺口与工具行为裁决分开

N02的R1/R2、局部Revise是题内既有弱卡未说清review及未覆盖婉拒的诊断，不是新的Skill失败。模型按要求揭示问题、不补写新卡、保持2/2预算，HR在D1披露之后才引用30K。因此本例PASS；不把诊断卡片缺口包装成卡片已经可直接使用。

## 文档收口

同步本版验收与发布说明，不改运行内容。N03/N04分别通过缺Brief与两项适用异议的原标准。所有原始输入输出、旧manifest、PARTIAL及服务失败保留；无新的模型调用或自动重跑。原生安装、CI、全场景／完整Full Loop回归仍NOT_RUN。

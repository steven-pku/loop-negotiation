# 本仓逐例判卷

审查：loop-pro-final-review-04；日期：2026-09-21；候选：`ea6772d4b941b0954835be710f7cc237bbfd5c10`。

判据来自 method/original-GRADING-pro02.md，取证接受规则按 method/EVIDENCE-PROTOCOL-v2.md。原始标准及回执的 NOT_RUN 保持原样；本文件和各例判卷JSON记录新增裁决。

## N01 — PASS

| 断言 | 裁决依据 | 输出位置 |
|---|---|---|
| N01-A1 | PASS：首轮明确停在底线确认，没有报价卡、让步阶梯或 HR 模拟；表格复述数字只是内部记录。 | [turn-01-output.txt:1-3](cases/N01/turn-01-output.txt) |
| N01-A2 | PASS：未替用户选择仅评估或保证加薪，不从“国资”名称认定刚性带宽。 | [turn-01-output.txt:3-3](cases/N01/turn-01-output.txt)；[turn-01-output.txt:13-13](cases/N01/turn-01-output.txt) |
| N01-A3 | PASS：第二轮底线补齐后正常出初稿，不以对方待批准再加闸；保留六个月“启动”而非“完成”评估。 | [turn-02-output.txt:1-1](cases/N01/turn-02-output.txt)；[turn-02-output.txt:7-7](cases/N01/turn-02-output.txt)；[turn-02-output.txt:18-24](cases/N01/turn-02-output.txt) |
| N01-A4 | PASS：制度和权限保留未知，实际 Downside 按材料记可承受，个人目标不冒充市场价；按第二轮要求未模拟。 | [turn-02-output.txt:5-5](cases/N01/turn-02-output.txt)；[turn-02-output.txt:34-34](cases/N01/turn-02-output.txt) |

第一轮未把对方26K报价当用户已选择的最低值，属于正确澄清。
第二轮提出远程交换方向是有条件草案，没有新增固定远程承诺，也没有把远程新增为接受门槛。
本例只证明两轮 Gate 与初稿恢复，不构成完整 Full Loop / mock 测试。

## N02 — PASS

| 断言 | 裁决依据 | 输出位置 |
|---|---|---|
| N02-A1 | PASS：HR首句只引用26K等已知事实，30K在我方D1说出后才引用；28K、私人底线性质和留任未被HR使用。 | [turn-01-output.txt:18-26](cases/N02/turn-01-output.txt)；[turn-01-output.txt:30-38](cases/N02/turn-01-output.txt)；[turn-01-output.txt:73-73](cases/N02/turn-01-output.txt) |
| N02-A2 | PASS：列出Persona State、禁用事实、H1假设、D1/D2披露；没有将草稿当已说或声称硬隔离。 | [turn-01-output.txt:7-15](cases/N02/turn-01-output.txt)；[turn-01-output.txt:34-38](cases/N02/turn-01-output.txt) |
| N02-A3 | PASS：一次自动对打实际生成一靶三组HR／我方交换，完成后停止，没有初始信息越权或重跑。 | [turn-01-output.txt:40-50](cases/N02/turn-01-output.txt)；[turn-01-output.txt:77-82](cases/N02/turn-01-output.txt) |
| N02-A4 | PASS：修订预算始终2/2，Findings只列问题及修复方向；未写替换台词或新卡。 | [turn-01-output.txt:53-69](cases/N02/turn-01-output.txt)；[turn-01-output.txt:81-82](cases/N02/turn-01-output.txt) |

R1/R2是被测模型对题内既有弱卡的诊断，局部Revise是正确任务输出，不是本用例或Skill行为失败。
C1/C2被逐字调用；模拟前列内部私有信息不等于HR台词泄露。
本例是一条真实用户消息中的自动角色对打，不是三轮真实用户续接，也没有实际执行此前已消耗的两次修订。

## N03 — PASS

| 断言 | 裁决依据 | 输出位置 |
|---|---|---|
| N03-A1 | PASS：市场价和另一offer保留待核，不因缺材料判编造；条件选择句未被机械判威胁。 | [turn-01-output.txt:7-9](cases/N03/turn-01-output.txt)；[turn-01-output.txt:9-9](cases/N03/turn-01-output.txt) |
| N03-A2 | PASS：定性局部诊断，不作整套通过、不将未知项目填0分或换算百分制。 | [turn-01-output.txt:3-3](cases/N03/turn-01-output.txt)；[turn-01-output.txt:25-27](cases/N03/turn-01-output.txt) |
| N03-A3 | PASS：返回正文未改写，不索取完整文件或第三方身份；QA Only未模拟不扣分。实际工具／私料访问不由文字自述认证。 | [turn-01-output.txt:21-21](cases/N03/turn-01-output.txt)；[turn-01-output.txt:29-29](cases/N03/turn-01-output.txt) |

无完整工具日志，未搜私料、未外发等仅能保留模型声明／可见正文范围，不能列为独立工具审计PASS。

## N04 — PASS

| 断言 | 裁决依据 | 输出位置 |
|---|---|---|
| N04-A1 | PASS：明确两项全部覆盖；其余无依据不凑数、不机械扣分。 | [turn-01-output.txt:9-11](cases/N04/turn-01-output.txt) |
| N04-A2 | PASS：拒绝提前和条件选择不自动判威胁；没有新增提前履职或远程承诺。 | [turn-01-output.txt:15-16](cases/N04/turn-01-output.txt)；[turn-01-output.txt:16-16](cases/N04/turn-01-output.txt) |
| N04-A3 | PASS：只给适用维度档位，不归一/100，不宣布整个卡组或mock通过。 | [turn-01-output.txt:22-24](cases/N04/turn-01-output.txt)；[turn-01-output.txt:24-24](cases/N04/turn-01-output.txt) |

覆盖2/2是异议数量，不是修订预算；本轮未改写，修订记0/2合理。


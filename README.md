# 大学《线性代数》题库刷题网页

同济大学《工程数学·线性代数》第六版配套题库，**500 题**（单选 84 · 多选 83 · 判断 83 · 填空 84 · 简答与名词解释 83 · 计算与分析 83），三难度分级，逐题解析 + 考点出处，其中 48 题标注「真题改编」（中科大历年考题汇编、考研数学真题、高校期末卷等）。

**在线使用**：打开 `index.html` 即可 —— 单文件、零外部依赖（KaTeX 与字体全部内联），断网可用，手机可用。

## 功能

- **两种练习模式**：单题聚焦（一屏一题，默认，推荐）与列表分页（每页 20 题）
- **答题卡**：500 题状态网格（未答 / 已答未判定 / 正确 / 错误），点击题号跳题
- **键盘快捷键**（单题模式）：`←` `→` 切题，`A`–`D` 选选项，`Enter` 确认多选
- **深色模式**：跟随系统自动切换，也可手动循环（自动 → 浅色 → 深色）
- **判分体系**：客观题自动判分（多选少选/错选均 0 分）；计算与分析题按采分点自评
- **错题本 / 统计面板**：跨会话累计，进度存浏览器 localStorage，多标签页写入自动合并

## 目录结构

```
index.html        成品（构建产物，部署即用它）
更新指南.md       日常更新 / 扩题的操作手册（先读这个）
tools/
  qa_bank/        题库源码（ch1.py…ch6.py 基础库 + ch*b.py 扩写章）
  qa_bank/target.py  题库口径的单一事实源（题量/配额/阈值只在这里改）
  template.html   页面骨架（占位符由构建脚本填充）
  assets/         app.js / app.css（界面与交互逻辑）
  build_quiz.py   构建：题库 + 内联 KaTeX → index.html
  update_site.py  一条命令跑完全部构建 + 六道验证门禁 + 暂存同步
  verify_quiz.py / audit_choice.py / audit_open.py / scan_escapes.py /
  diff_bank.py / check_html.py   质量门禁（SymPy 数值复核 542 条等）
  research/       真题素材摘要、现有题干清单
```

## 改题 / 扩题（三步）

```powershell
# 1. 改 tools/qa_bank/ch*.py（题目内容）或 tools/assets/（界面）
# 2. 题库有增删时刷新口径：
python tools/tally.py --emit-target     # 把打印的常量块粘进 tools/qa_bank/target.py
# 3. 构建 + 全部门禁：
python tools/update_site.py
```

任何一道门禁不过都会中止、不会产出可发布的成品。详细说明见 `更新指南.md`。

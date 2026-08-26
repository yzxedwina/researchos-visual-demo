# ResearchOS — AI Research Intelligence Platform

## 打开方式

直接双击 `index.html`，或将它拖入浏览器即可。

## 产品流程

1. 在 Research Setup 导入 WoS/Scopus CSV 或 TXT 文件并确认研究上下文；文件只在当前浏览器标签页中处理。
2. 编辑三类 Context，点击 `Confirm setup`。
3. Literature Screening → 对文献做 Include / Exclude / Boundary 判断。
4. 接受或编辑 Adaptive Context 建议，生成 Context v2。
5. 完成剩余筛选并冻结 Final Corpus。
6. 在 Bibliometric Explorer 浏览年度趋势、关键词、作者合作及主题聚类。
7. 在 Research Intelligence 审阅、编辑并验证带证据的 AI 洞察。

界面右上角可切换中文与 English，默认语言为中文。

## 当前本地版能力

- 支持知网、WoS、Scopus 常见 CSV、制表符 TXT，以及 WoS tagged text。
- 支持 EndNote Tagged Text（`.txt`/`.enw`）和 RIS（`.ris`），自动映射题名、作者、年份、期刊、关键词、摘要、DOI 和记录号。
- 知网原生字段可直接映射：题名/篇名、摘要、作者、出版年/发表时间/年卷期、关键词/主题词、刊名/来源、DOI、被引频次和记录号等。
- 自动映射题名、摘要、作者、年份、关键词、来源、DOI、引用次数等常见字段，并按 DOI/题名去重。
- 在浏览器内生成筛选建议；研究者可逐篇改为 Include、Exclude 或 Boundary。
- 冻结 Final Corpus 后，基于实际纳入文献重新计算年度趋势、关键词共现、作者合作和 TF-IDF + k-means 主题聚类。
- 分析结果和洞察都可回溯到当前语料库中的统计、主题簇、作者或文献记录。

建议先使用 500–1000 篇数据。较大文件会增加浏览器计算和渲染时间；作者消歧和聚类主题命名仍需研究者复核。

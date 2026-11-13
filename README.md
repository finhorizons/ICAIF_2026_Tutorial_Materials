<div align="center">

# Trustworthy Document Intelligence in Finance

**A hands-on tutorial at ACM ICAIF 2026**<br>
Milan · Saturday 14 November 2026, 08:30–10:30 CET · Room 3, Bocconi University

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/finhorizons/ICAIF_2026_Tutorial_Materials/blob/main/notebook/trustworthy_docai_tutorial.ipynb) [![Website](https://img.shields.io/badge/website-docai.finhorizons.org-C2410C)](https://docai.finhorizons.org) [![Code: MIT](https://img.shields.io/badge/code-MIT-1F2937)](LICENSE) [![Text and slides: CC BY 4.0](https://img.shields.io/badge/text%20and%20slides-CC%20BY%204.0-1F2937)](https://creativecommons.org/licenses/by/4.0/)

</div>

Question answering over company filings is one of the most common uses of large language models in finance, and a wrong number there is costly. In this tutorial we build a question-answering system over real SEC filings. Every number in its answers can be traced back to the table cell or sentence it comes from. We then measure how faithful the answers are, and fix what breaks.

The running example is NVIDIA: its Form 10-K for fiscal year 2026, the press release and CFO commentary of its fourth quarter, and a later Form 10-Q, all public documents from SEC EDGAR.

## Start here

| Material | Where |
| --- | --- |
| **Slides** | [HTML](slides/html/ICAIF2026_Trustworthy_DocAI_Tutorial.html) · [PDF](slides/pdf/ICAIF2026_Trustworthy_DocAI_Tutorial.pdf) · [PowerPoint](slides/ppt/ICAIF2026_Trustworthy_DocAI_Tutorial.pptx). The HTML version is one file: download it and open it in Chrome. Most pages can be clicked, and the three exercises run inside the slides. |
| **Notebook** | [Open in Colab](https://colab.research.google.com/github/finhorizons/ICAIF_2026_Tutorial_Materials/blob/main/notebook/trustworthy_docai_tutorial.ipynb). It replays our recorded run, so it needs no GPU and returns the numbers on the slides. |
| **Evaluation checklist** | [docai.finhorizons.org/checklist](https://docai.finhorizons.org/checklist/): 250 checks for evaluating question answering over financial filings, each with what went wrong in our system and what we do now. |
| **Resource hub** | [docai.finhorizons.org/resources](https://docai.finhorizons.org/resources/): more than 800 papers, tools and data sets, each placed at its step of the pipeline. |
| **Website** | [docai.finhorizons.org](https://docai.finhorizons.org): the program, the presenters and everything above. |

## What the tutorial covers

| Part | What you learn | Exercise in the slides |
| --- | --- | --- |
| **1 · Parsing, chunking and indexing** | How a filing becomes text, tables and searchable pieces that keep their source | Parse, chunk and index the 10-K |
| **2 · Retrieval, generation and numeric grounding** | How the system finds the right pieces, writes an answer with citations, and checks every number against its source | Retrieve, generate and check the numbers |
| **3 · Faithfulness evaluation** | How to score answers with rules and with an LLM judge, and how to turn the worst answer into a fix | Find the worst answer, name its cause, fix it |
| **4 · Production concerns** | What information was available on a given date, how fast the library is updated, waiting time and cost, where each number came from, and the rules for responsible use | No exercise |

## What is in this repository

```
slides/
  html/ICAIF2026_Trustworthy_DocAI_Tutorial.html   the slides as one self-contained file
  pdf/ICAIF2026_Trustworthy_DocAI_Tutorial.pdf     the slides as PDF
  ppt/ICAIF2026_Trustworthy_DocAI_Tutorial.pptx    the slides as PowerPoint
notebook/
  trustworthy_docai_tutorial.ipynb                 the Colab notebook
  llm_cache.json                                   the recorded run behind the slides
  corpus/                                          the filings, the XBRL company facts and the evaluation set
```

## Run the notebook

Open the notebook in Colab and run the cells from top to bottom. By default it **replays the recorded run** behind the slides: the model's answers and the retrieval results come from `notebook/llm_cache.json`, so every cell returns quickly and the numbers match the slides. No GPU and no API key are needed.

To run the models yourself, choose a **T4 GPU** runtime (the free tier is enough) and run `%env DOCAI_LLM_CACHE=record` in a cell before Section 0. A full run takes about an hour with the default open-source models: `Qwen/Qwen2.5-3B-Instruct` writes the answers, `BAAI/bge-small-en-v1.5` and `BAAI/bge-reranker-base` find the pieces, and `Qwen/Qwen2.5-7B-Instruct` (4-bit) is the judge.

If you change a prompt or ask a new question, the recording cannot answer it. gpt-oss-120b, OpenAI's open-weight model, then answers over Groq's free API: get a key at console.groq.com and add it as `GROQ_API_KEY` in the Colab secrets panel. To use a commercial model instead, set `LLM_BACKEND` in the first code cell to `anthropic` or `openai` and add your key in the same panel.

<details>
<summary>Environment variables</summary>

`DOCAI_LLM_CACHE` (`replay`, the default, `record` or `off`), `DOCAI_QUICK=1` (5 questions instead of 14), `DOCAI_LLM_BACKEND`, `DOCAI_HF_MODEL`, `DOCAI_EMBED_MODEL`, `DOCAI_RERANK_MODEL`, `DOCAI_JUDGE_MODEL`, `DOCAI_JUDGE_4BIT=0`, `DOCAI_MAX_NEW_TOKENS`, `DOCAI_OPENAI_MODEL`.

</details>

## The data

All documents are public filings of NVIDIA Corporation on SEC EDGAR (CIK 0001045810). `notebook/corpus/README.md` gives the original link of each one and the rules for downloading from EDGAR yourself.

| Document | Period |
| --- | --- |
| Form 10-K | fiscal year 2026, ended 25 January 2026 |
| Earnings press release (8-K, Exhibit 99.1) | fourth quarter of fiscal 2026 |
| CFO commentary (8-K, Exhibit 99.2) | fourth quarter of fiscal 2026 |
| Form 10-Q | second quarter of fiscal 2027, ended 26 July 2026 |
| XBRL company facts | fiscal 2025 onwards |

The evaluation set, `notebook/corpus/eval/questions.json`, has 15 analyst-style questions with gold answers written by hand from these documents. Each question lists the figures a faithful answer must contain and the place it should cite. Earnings-call transcripts are not freely licensed, so they are not included.

The recorded run was made on a Colab T4 on 6 November 2026, with the models named above, on 14 of the 15 questions.

## Organizers and presenters

**Organizers:** Yaxuan Kong (University of Oxford), Yichen Li (FinHorizons Foundation) and Stefan Zohren (University of Oxford)<br>
**Presenters:** Yaxuan Kong and Yichen Li

## About the FinHorizons Foundation

The [FinHorizons Foundation](https://finhorizons.org) is an open research community for responsible AI in finance, and the home of this tutorial. Every Saturday on Zoom we hold either a seminar, where researchers and practitioners talk about their work on AI in finance, or a reading group, where several people present recent papers on one topic and we discuss them together. Every talk is recorded, and the slides stay online.

You are welcome to join us: [finhorizons.org](https://finhorizons.org) has the schedule and how to take part. For questions about the tutorial, write to events@finhorizons.org.

## Citation

If you use these materials, please cite the tutorial:

```bibtex
@misc{kong2026trustworthy,
  title        = {Trustworthy Document Intelligence in Finance},
  author       = {Kong, Yaxuan and Li, Yichen and Zohren, Stefan},
  year         = {2026},
  howpublished = {Tutorial at the 7th ACM International Conference on AI in Finance (ICAIF 2026), Milan},
  url          = {https://docai.finhorizons.org}
}
```

## License

The code (the notebook) is under the MIT license, see `LICENSE`. The text, the slides and the evaluation set are under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/): you may share and adapt them if you name the authors above. The SEC filings in `notebook/corpus/` are public records of the U.S. Securities and Exchange Commission and are not covered by either license.

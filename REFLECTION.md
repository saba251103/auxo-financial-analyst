# REFLECTION.md

## 1. What makes your chatbot feel intelligent rather than just doing keyword search? What did you specifically do to get there?

I wanted the chatbot to behave more like a financial analyst rather than a simple document search tool.

Instead of sending every query through the same pipeline, I created different engines for different kinds of questions. For example, structured financial questions like revenue or EPS are answered directly from the spreadsheet data, stock-related questions use the CSV data, and qualitative questions like strategy or risks use document retrieval with Gemini.

For broader questions that need reasoning across multiple sources, I added a multi-source pipeline that combines financial data, stock performance, and document evidence before generating a response.

I also added follow-up memory so the chatbot can handle conversational questions like “Compare with FY25” without needing the full context again.

Another thing I focused on was output format selection. Instead of making the user choose, the chatbot decides whether the answer should be plain text, a PDF summary, or an Excel file depending on the query.

Overall, the goal was to make the system choose how to think, not just what to retrieve.

---

## 2. Where does it still fall short? What would a real analyst notice that the system gets wrong or misses?

There are definitely areas where the system can improve.

The routing logic is still rule-based, so unusual or ambiguous questions can sometimes be misclassified. I fixed several of these during testing, but it’s not perfect.

Document retrieval also depends on chunk relevance, which means the chatbot may sometimes retrieve less useful sections instead of the strongest evidence.

The chatbot is good at summarizing and comparing data, but it’s not doing deep financial analysis like valuation models, forecasting, peer comparisons, or scenario analysis the way a real analyst would.

Follow-up memory works for short conversations, but it’s fairly lightweight and not built for very long analytical discussions.

I also found that combining multiple evidence sources was trickier than expected because structured data, stock analytics, and document retrieval all had different formats internally. Some debugging was needed to make sure valid evidence actually reached the response layer.

Finally, citation formatting depends partly on prompt behavior, so while the system is grounded, source presentation is not fully hard-enforced in every edge case.

---

## 3. Which AI tools did you use to build this, and what did you have to fix or override yourself?

I used Google Gemini API for reasoning, summarization, and analyst-style responses.

For document understanding, I used vector retrieval with embeddings over the PDF documents.

For structured financial and stock analysis, I avoided relying on the LLM and used deterministic logic instead, since numeric questions are better handled directly.

A lot of the actual work was in engineering rather than just calling AI APIs. This included:

- designing query routing
- handling follow-up memory
- building separate processing pipelines
- fixing evidence schema mismatches
- improving routing errors
- fixing export generation issues
- making Gemini work only with grounded evidence

The biggest takeaway was that building a chatbot that looks smart is easy, but making it reliable across multiple data types and query styles takes much more careful system design.

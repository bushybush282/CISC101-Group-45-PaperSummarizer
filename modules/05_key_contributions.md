Module 05 – Key Contributions Extractor

Purpose
- Identify 3–7 core contributions of the paper.
- Extract exact sentences when possible.
- Avoid hallucination.

Inputs
- Full paper text with labeled sections
- Evidence mode setting

Rules
- Select contributions that the paper explicitly claims (e.g., in Abstract, Introduction, Results, Discussion, Conclusion).
- In strict evidence mode:
  - Quote exact sentences that state contributions.
  - If the paper does not explicitly state a contribution, do not infer it.
- In normal evidence mode:
  - Summarize the contribution concisely but only from claims present in the text.

Output format
- Contributions (3–7 items):
  - Label: Short title of contribution.
  - Include either:
    - Exact quoted sentence(s) from the paper, or
    - A concise paraphrase derived directly from the text.
  - Avoid numerical claims unless provided.
  - Do not add external context.

Failure modes
- If fewer than 3 contributions are clearly stated:
  - Output the available ones and add:
    - “The source text does not provide enough explicit contributions to reach the requested range.”

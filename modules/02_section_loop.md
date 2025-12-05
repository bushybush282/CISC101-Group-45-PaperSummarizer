Module 02 – Section Loop

Purpose
- Loop over all sections in order.
- Perform summarization with constraints.
- Support summary_level modes.
- Produce warnings for short or missing sections.

Inputs
- Normalized section array from Module 01
- summary_level (“short” | “detailed”)
- evidence_mode (“normal” | “strict”)

Summarization rules
- Word limit: Each section summary ≤ 150 words.
- Evidence rules: If strict, only use claims present verbatim or clearly supported; otherwise output:
  - “The source text does not provide enough detail to summarize this section in strict evidence mode.”
- Missing text: If no usable text, output:
  - “Section skipped: no usable text was provided.”
- Short text (<50 words): Include warning line:
  - “Section very short: summary may be incomplete.”

Mode behaviors
- summary_level = short:
  - Produce 1–2 sentences focusing on the section’s core purpose, key idea, and essential definition(s) present in the text.
  - Keep within the 150-word cap.
- summary_level = detailed:
  - Produce a small paragraph (3–5 sentences) plus 3–5 bullet points highlighting:
    - Key ideas
    - Methods or approaches
    - Core results or conclusions
    - Important definitions
    - Limitations stated in the section
  - Keep total prose ≤ 150 words per section; bullets count toward this limit, so be concise.

Procedure
1. For each section in the provided order:
  - Read the section text.
  - If missing/empty: emit standardized skip message.
  - If strict evidence mode and claims are unclear/not present: emit strict-evidence insufficiency message.
  - Apply summary_level formatting.
  - Enforce the 150-word maximum (truncate gracefully if needed, preserving sense).
  - Add a “Section very short” warning if word_count < 50.
  - Store summary and any warnings for rendering.

2. Definitions handling:
  - Extract definitions only if the section text explicitly defines the term.
  - Do not infer new terms or meanings.

3. Consistency:
  - Maintain original section order in output.


Mode behaviors
- summary_level = short:
  - Produce 1–2 sentences focusing on the section’s core purpose, key idea, and essential definition(s) present in the text.
  - Keep within the 150-word cap.
- summary_level = detailed:
  - Produce a small paragraph (3–5 sentences) plus 3–5 bullet points highlighting:
    - Key ideas
    - Methods or approaches
    - Core results or conclusions
    - Important definitions
    - Limitations stated in the section
  - Keep total prose ≤ 150 words per section; bullets count toward this limit, so be concise.

Module 03 – Guardrails

Purpose
- Enforce strict evidence mode.
- Prevent hallucinations and invented citations or results.
- Standardize warnings.

Core rules
- Only summarize available text: No external knowledge or inference beyond plain restatement.
- Never invent citations or results: If citations or numerical results are not shown, do not fabricate them.
- Never hallucinate sections: If a section is not provided, do not create it; instead warn.

Strict evidence mode
- Include only claims found exactly or directly supported by the text.
- If insufficient information:
  - Output: “The source text does not provide enough detail to summarize this section in strict evidence mode.”

Standardized warning messages
- Missing section or empty text:
  - “Section skipped: no usable text was provided.”
- Short sections (<50 words):
  - “Section very short: summary may be incomplete.”

Enforcement
- Validate each section summary against the 150-word limit.
- Validate presence of claims in strict mode before inclusion.
- Preserve the user-provided section order.
- Record all warnings for Module 04 rendering.


Strict evidence mode
- Activate when `evidence_mode = "strict"`.
- Include only claims, equations, and results that appear in the provided text or are directly supported by it.
- Do not infer missing logic, context, or background not present in the source section.
- If there is not enough information to summarize while maintaining strict evidence limits:
  - Output:  
    **“The source text does not provide enough detail to summarize this section in strict evidence mode.”**

Standardized warning messages
- Missing section or empty text:
  - Output: **“Section skipped: no usable text was provided.”**
- Short sections (<50 words):
  - Output: **“Section very short: summary may be incomplete.”**
- These warnings must be emitted exactly and consistently whenever their conditions apply.

  

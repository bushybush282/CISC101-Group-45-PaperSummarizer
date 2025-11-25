Module 01 – Intake & Setup

Purpose
- Normalize section names.
- Detect missing, empty, or under-50-word sections.
- Prepare variables including summary_level and evidence_mode.

Inputs
- Paper text (full or section-labeled chunks)
- Ordered section list
- Target audience (expert or lay)
- Summary length mode (short or detailed)
- Evidence mode (normal or strict)

Steps
1. Normalize section names:
  - Map common variants to canonical names:
    - Introduction: “Intro,” “Background”
    - Methods: “Method,” “Materials and Methods,” “Approach,” “Experimental Setup”
    - Results: “Findings,” “Outcomes”
    - Discussion: “Analysis,” “Interpretation,” “Implications”
    - Conclusion: “Conclusions,” “Summary,” “Closing Remarks”
    - Abstract: “Summary (Abstract)”
    - Related Work: “Literature Review”
    - Limitations: “Constraints,” “Weaknesses”
    - Future Work: “Outlook,” “Next Steps”
    - Appendix: “Supplement”
- Preserve original order from the user-provided section list.

2. Bind configuration variables:
  - summary_level: “short” or “detailed”
  - evidence_mode: “normal” or “strict”
  - audience: “expert” or “lay”

3. Section presence and length checks:
  - For each section in the list:
    - Determine if text exists; if missing, record warning:
      - “Section skipped: no usable text was provided.”
    - If text exists but is empty or whitespace, record same warning.
    - If word count < 50, record warning:
      - “Section very short: summary may be incomplete.”

4. Data preparation:
  - Store a clean array of {section_name, text, word_count, status_flags}.
  - Store warnings separately for downstream rendering.

5. Validation:
  - Ensure per-section text is only the provided content; no external augmentation.
  - Confirm summary_length and evidence_mode are set; if not, default:
    - summary_level = “short”
    - evidence_mode = “normal”
  - Confirm section order equals the provided order; never reorder.

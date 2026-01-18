# Process and Tooling

This repository was created using an **AI-assisted, human-directed workflow** involving collaboration between the human author and two AI systems (ChatGPT and Claude).

The conceptual vision, research questions, validation methodology, and all execution were human-directed. AI systems were used as specialized tools for code generation, documentation synthesis, and structural organization.

---

## Role of the human author

The human author's role included:

- **Defining the research objective**: Map GR's failure manifold through computational stress tests
- **Directing the research process**: Iteratively guiding what types of failures to explore and how to probe them
- **Making all conceptual decisions**: What constitutes a "failure," how to classify it, what questions to ask next
- **Consulting additional AI tools**: Using Perplexity for research ideas, sanity checks on toy directions, and validation that data interpretations are headed in the right direction
- **Executing all toy models**: Running every Python script to generate the JSON outputs (all 90 toys)
- **Quality control**: Ensuring alignment between code, outputs, documentation, and interpretive claims
- **Final approval**: All content, classifications, and conclusions reviewed and approved by the human author

---

## Role of ChatGPT

ChatGPT was used for **toy model generation and initial descriptions**:

### Toy Development (Toys 001-090)
- **Conceptual design**: Human author posed research questions; ChatGPT suggested which toy models would expose specific failure modes
- **Python implementation**: ChatGPT wrote all 90 Python toy scripts under human direction
- **Output validation**: After human execution, ChatGPT compared JSON outputs against Python source code to verify correctness, expected field structure, and diagnostic accuracy
- **Iterative refinement**: Human author reviewed validation results, identified gaps, directed creation of additional toys

### Initial Documentation (TOYS_LEGACY.md)
- ChatGPT created early toy descriptions (v1.0-v1.1.5)
- These were functional but lacked interpretive depth needed for full understanding

### Comprehensive Redescription (v1.1.6)
Using the workflow defined in `MAKE.md` (see `/toys/MAKE.md`):
1. Human author provided ChatGPT with:
   - Python source code for each toy
   - JSON output files from execution
   - `MAKE.md` specification for documentation format
2. ChatGPT generated complete toy descriptions (all 90) following the specification
3. ChatGPT validated descriptions against actual JSON outputs

ChatGPT did **not** autonomously define research goals, select failure modes to investigate, or make decisions without human direction.

---

## Role of Claude

Claude was used for **documentation architecture and interpretive synthesis**:

### Documentation Structure (v1.1.6)
- Human author provided Claude with all 90 toy descriptions from ChatGPT
- Claude organized them into the `/docs/` structure:
  - 13 thematic phase files
  - Navigation indices (by spacetime, by toy number, by failure mode)
  - User guides (getting started, JSON interpretation, common pitfalls)
- Claude created the professional documentation hierarchy

### Repository Documentation
- Main `README.md` in GitHub root
- Release notes for version updates
- Structural organization of repository

### Interpretive Analysis (SPECULATION folder - Legacy)
- Claude wrote all speculative analysis in `SPECULATION/` folder (v1.1.0-v1.1.5)
- This included interpretive synthesis about emergence, effective theory status, etc.
- **Status**: Legacy content, retained for reference but not updated in v1.1.6
- **Future**: Human author plans to have Claude regenerate updated interpretive analysis

Claude did **not** generate toy models, execute code, or make empirical claims without human review.

---

## Workflow Summary

**Phase 1: Toy Creation (ChatGPT + Human)**
1. Human defines research question or failure mode to explore
2. ChatGPT proposes toy model approach
3. ChatGPT implements Python script
4. Human executes script → generates JSON output
5. ChatGPT compares JSON output to Python source to validate correctness
6. If validation passes → move to next toy; if issues found → refine and repeat
7. Repeat for all 90 toys

**Phase 2: Comprehensive Description (ChatGPT + Human)**
1. Human provides ChatGPT with:
   - `MAKE.md` specification (see `/toys/MAKE.md`)
   - Python source file
   - JSON output file
2. ChatGPT generates detailed toy description following spec
3. ChatGPT validates description against JSON outputs
4. Repeat for all 90 toys

**Phase 3: Documentation Architecture (Claude + Human)**
1. Human provides Claude with all 90 descriptions
2. Claude organizes into `/docs/` structure
3. Claude creates navigation aids and user guides
4. Claude writes main README and release notes
5. Human reviews and approves documentation

**Phase 4: Interpretive Synthesis (Claude + Human - Future)**
- Planned: Claude will regenerate `SPECULATION/` analysis
- Human will direct interpretive scope and validate conclusions

---

## Division of Labor

| Task | Human | ChatGPT | Claude |
|------|-------|---------|--------|
| Define research objectives | ✓ | | |
| Decide what toys to create | ✓ | Suggest | |
| Implement Python toys | | ✓ | |
| Execute Python scripts | ✓ | | |
| Generate JSON outputs | ✓ | | |
| Validate JSON vs Python | | ✓ | |
| Write toy descriptions | | ✓ | |
| Organize documentation | | | ✓ |
| Create navigation indices | | | ✓ |
| Write user guides | | | ✓ |
| Write README/release notes | | | ✓ |
| Write interpretive analysis | | | ✓ |
| Review final documentation | ✓ | | |
| Make final decisions | ✓ | | |

---

## Validation and Responsibility

All content in this repository was validated through a multi-stage process:

**Technical Validation (ChatGPT):**
- JSON outputs compared against Python source code for correctness
- Field structure and diagnostic contents verified
- Expected behavior and numerical outputs checked

**Content Validation (Human):**
- Conceptual correctness: Do toys test what they claim to test?
- Interpretive accuracy: Do descriptions reflect what diagnostics actually show?
- Internal consistency: Do classifications align across all 90 toys?
- Pedagogical clarity: Is documentation accessible and complete?

**Responsibility for the correctness, framing, and interpretation of the work rests entirely with the human author.**

---

## Motivation for Disclosure

This file exists to:

1. **Document the process transparently**: How AI tools were used in this project
2. **Clarify roles**: What was human judgment vs AI assistance
3. **Enable reproducibility**: Others can follow similar workflows
4. **Acknowledge tools**: AI systems as specialized instruments in research

This disclosure is made in the spirit of scientific transparency, not to promote or diminish the use of AI tools. The project stands on its technical and conceptual merits.

---

## Scope Note

This repository does not make empirical claims, propose new physical laws, or replace existing theories. It is a **diagnostic and classificatory exercise** focused on mapping where and how classical General Relativity loses predictive or operational meaning.

All toys are **stress tests**, not predictions. All outputs are **diagnostics**, not measurements. All interpretations are **conditional**, not definitive.

---

## Version History of Process

- **v1.0.0** (Initial): ChatGPT created 64 toys with basic descriptions (TOYS_LEGACY.md)
- **v1.1.0-v1.1.5**: Claude added interpretive synthesis (SPECULATION folder)
- **v1.1.6**: Complete workflow overhaul
  - ChatGPT redescribed all 90 toys using MAKE.md specification
  - Claude organized into professional documentation structure
  - Human validated all content end-to-end

---

## Tools Used

- **ChatGPT** (OpenAI): Python code generation, toy descriptions
- **Claude** (Anthropic): Documentation architecture, interpretive synthesis
- **Perplexity**: Research consultation, toy idea generation, directional validation
- **Python 3.x**: All toy implementations
- **JSON**: Structured output format
- **Markdown**: Documentation format
- **Git/GitHub**: Version control and distribution

# Homework Assignment: The Prompt Ladder
**Track:** Machine Learning / AI Developer
**Task:** Build a 5-step prompt ladder to transition a weak, generic prompt into a high-performing, highly-targeted engineered prompt, documenting the output differences and notes at each step.

---

## The Baseline (Weak Prompt)
*   **Prompt:** "Translate this job description into simple terms: 'Leverage deep synergies across cross-functional teams to coordinate and optimize agile paradigms, ensuring maximum velocity and alignment with enterprise stakeholders.'"
*   **Output:** 
    > "This means you will collaborate closely with various departments to organize and improve project workflows using agile methodologies. Your goal is to make sure tasks are completed as quickly as possible and that everyone, including business leaders and key partners, is kept updated and on the same page."
*   **Notes:**
    *   **What changed in the prompt:** Nothing. This is our starting, lazy benchmark.
    *   **What actually improved in the output:** N/A (this is our starting baseline).
    *   **What still failed:** It is incredibly wordy, dry, and reads like a generic HR textbook. It replaced corporate buzzwords with *more* corporate buzzwords (like "collaborate closely," "methodologies," and "key partners"). It doesn't tell us what a developer actually does.
    *   **What to try next:** We need to add a clearer goal to strip the fluff and focus purely on raw, day-to-day actions.

---

## Step 1: Clearer Goal
*   **Prompt:** "Translate this, but strip away all corporate jargon and focus purely on the practical, day-to-day work tasks: 'Leverage deep synergies across cross-functional teams to coordinate and optimize agile paradigms, ensuring maximum velocity and alignment with enterprise stakeholders.'"
*   **Output:** 
    > "Your daily work involves talking directly with other teams to coordinate project tasks, running team meetings (like standups), keeping the project moving forward quickly, and giving progress updates to the managers."
*   **Notes:**
    *   **What changed in the prompt:** Added a specific goal to strip corporate jargon and target practical, day-to-day work tasks.
    *   **What actually improved in the output:** It stopped using academic HR-speak. Phrases like "collaborate closely with various departments" turned into "talking directly with other teams," and "agile methodologies" turned into "running team meetings (like standups)."
    *   **What still failed:** It's still formatted as a boring, flat block of text. For a user scanning job descriptions quickly on a dashboard, a paragraph is too slow to read.
    *   **What to try next:** We need to add a specified output format (a Markdown table) to make this visually scannable.

---

## Step 2: Specified Output Format
*   **Prompt:** "Translate this, strip away corporate jargon, and focus on practical day-to-day tasks. Format your response as a clean Markdown table with two columns: 'What they wrote' and 'What you actually do': 'Leverage deep synergies across cross-functional teams to coordinate and optimize agile paradigms, ensuring maximum velocity and alignment with enterprise stakeholders.'"
*   **Output:**
    | What they wrote | What you actually do |
    | :--- | :--- |
    | Leverage deep synergies across cross-functional teams | Talk directly with other teams to coordinate project tasks. |
    | Coordinate and optimize agile paradigms, ensuring maximum velocity | Run team meetings (like standups) and keep the project moving forward quickly. |
    | Alignment with enterprise stakeholders | Give progress updates to the managers. |
*   **Notes:**
    *   **What changed in the prompt:** Added a Specified Output Format—asking for a clean, two-column Markdown table mapping "What they wrote" to "What you actually do."
    *   **What actually improved in the output:** The visual layout is now perfect. It is instantly scannable, letting a job seeker see the translation of each corporate phrase side-by-side.
    *   **What still failed:** The translations in the right column are still a bit too polite and generic ("coordinate project tasks," "keep the project moving forward"). We want it to sound like a real, blunt developer talking shop, not a textbook.
    *   **What to try next:** We will add a strict constraint to force the AI to be extremely brief.

---

## Step 3: Strict Constraints (The Setback)
*   **Prompt:** "Translate this, strip away corporate jargon, and focus on practical day-to-day tasks. Format your response as a clean Markdown table with two columns: 'What they wrote' and 'What you actually do'. Constraint: You must explain the daily task in exactly 5 words or less per row. Use zero professional buzzwords. : 'Leverage deep synergies across cross-functional teams to coordinate and optimize agile paradigms, ensuring maximum velocity and alignment with enterprise stakeholders.'"
*   **Output:**
    | What they wrote | What you actually do |
    | :--- | :--- |
    | Leverage deep synergies across cross-functional teams | Talk to other teams. |
    | Coordinate and optimize agile paradigms, ensuring maximum velocity | Run standard team meetings. |
    | Alignment with enterprise stakeholders | Email updates to bosses. |
*   **Notes:**
    *   **What changed in the prompt:** Added a strict Constraint—forcing the translation to be exactly 5 words or less per row and forbidding any professional buzzwords.
    *   **What actually improved in the output:** It is incredibly short, and all fluff is completely gone.
    *   **What still failed (The Setback):** This constraint actually made the output worse. By restricting the AI to just 5 words, it lost all practical developer context. "Run standard team meetings" is too vague—it doesn't capture *why* or *how* that relates to "optimizing agile paradigms" or shipping software, and "Talk to other teams" is too generic. We over-constrained it and lost the value.
    *   **What to try next:** We need to loosen the length limit slightly (to under 12 words) and add a Persona and Audience (acting as a blunt, technical team lead mentoring a junior dev) so the language sounds conversational and gritty.

---

## Step 4: Stated Persona & Audience
*   **Prompt:** "Act as a blunt, technical team lead mentoring a junior developer. Translate this, stripping away corporate jargon to expose only the practical, day-to-day tasks. Format your response as a clean Markdown table with two columns: 'What they wrote' and 'What you actually do'. Constraint: Keep 'What you actually do' under 12 words, using direct, gritty, conversational developer language. : 'Leverage deep synergies across cross-functional teams to coordinate and optimize agile paradigms, ensuring maximum velocity and alignment with enterprise stakeholders.'"
*   **Output:**
    | What they wrote | What you actually do |
    | :--- | :--- |
    | Leverage deep synergies across cross-functional teams | Slack other teams so we don't break each other's code. |
    | Coordinate and optimize agile paradigms, ensuring maximum velocity | Run daily standups to clear blockers and ship code faster. |
    | Alignment with enterprise stakeholders | Keep the bosses happy by translating tech updates into plain English. |
*   **Notes:**
    *   **What changed in the prompt:** Added a specific Persona & Audience (blunt technical team lead mentoring a junior developer) and slightly loosened the length constraint to 12 words.
    *   **What actually improved in the output:** The tone is absolutely perfect. It completely bypasses dry textbook phrases and uses actual developer-to-developer language ("Slack other teams," "break each other's code," "clear blockers," "ship code").
    *   **What still failed:** While this specific execution was excellent, running it across different text segments could lead to stylistic drift if the AI doesn't have a solid baseline example.
    *   **What to try next:** Add a few-shot example to cement the exact style and grit we expect in the translations.

---

## Step 5: Few-Shot Examples (Final Polish)
*   **Prompt:** "Act as a blunt, technical team lead mentoring a junior developer. Translate this, stripping away corporate jargon to expose only the practical, day-to-day tasks. Format your response as a clean Markdown table with two columns: 'What they wrote' and 'What you actually do'. Constraint: Keep 'What you actually do' under 12 words, using direct, gritty, conversational developer language. 

    **Example of what good looks like:**
    *   *What they wrote:* "Utilize cutting-edge paradigm shifts to optimize pipeline throughput."
    *   *What you actually do:* "Fix the slow CI/CD build scripts so deployments don't drag."

    Translate this: 'Leverage deep synergies across cross-functional teams to coordinate and optimize agile paradigms, ensuring maximum velocity and alignment with enterprise stakeholders.'"
*   **Output:**
    | What they wrote | What you actually do |
    | :--- | :--- |
    | Leverage deep synergies across cross-functional teams | Talk to other teams so you don't step on each other's toes. |
    | Coordinate and optimize agile paradigms, ensuring maximum velocity | Run daily standups and clear blockers to ship code on time. |
    | Alignment with enterprise stakeholders | Keep the bosses happy by translating tech updates into plain English. |
*   **Notes:**
    *   **What changed in the prompt:** Provided a clear, practical few-shot example to set the quality standard.
    *   **What actually improved in the output:** The AI nailed the exact balance of developer-centric grit, humor, and clarity on the very first run. 
    *   **What still failed:** Nothing—this is an outstanding, production-ready output layout.
    *   **What to try next:** Package this into a clean, reusable template that a stranger could run.

------

## 🤖 Cross-Model Comparison (ChatGPT vs. Claude)

To test the robustness and portability of our engineered prompt, the final Step 5 prompt was executed on both **ChatGPT (GPT-4o)** and **Claude**. 

### The Raw Outputs

#### ChatGPT (GPT-4o) Output:
| What they wrote | What you actually do |
| :--- | :--- |
| Leverage deep synergies across cross-functional teams | Talk to other teams and unblock work. |
| Coordinate and optimize agile paradigms | Run standups, plan sprints, keep tickets updated. |
| Ensuring maximum velocity | Remove blockers so developers ship faster. |
| Alignment with enterprise stakeholders | Keep managers informed and negotiate changing priorities. |

#### Claude Output:
| What they wrote | What you actually do |
| :--- | :--- |
| Leverage deep synergies across cross-functional teams to coordinate and optimize agile paradigms, ensuring maximum velocity and alignment with enterprise stakeholders. | Sync sprints with product/ops/marketing, ship code fast, keep leadership informed. |

*Translation: You're basically gluing together people from different departments so everyone ships stuff on time and leadership doesn't freak out. Agile "paradigms" = sprint ceremonies. "Velocity" = how much code lands each week. "Stakeholders" = your boss's boss.*

---

### Detailed Analysis & Comparison

| Metric | ChatGPT (GPT-4o) | Claude (Anthropic) |
| :--- | :--- | :--- |
| **Constraint Adherence** | **Excellent (Structural) / Weak (Tone)**<br>Strictly adhered to the table structure, separating the source text into clean rows. It respected the "under 12 words" constraint. | **Weak (Structural) / Excellent (Tone)**<br>Failed the structural constraint entirely. Instead of mapping row-by-row, it jammed the whole prompt into one row and dumped prose text below the table. |
| **Tone & Persona** | **Too Corporate/Polite**<br>Despite being told to be a "blunt, gritty mentor," it drifted back to safe HR phrases like "negotiate changing priorities" and "keep managers informed." | **Incredibly Gritty & Authentic**<br>Nailed the blunt developer lead voice perfectly. Phrases like "gluing together people," "leadership doesn't freak out," and calling out "your boss's boss" are highly realistic. |
| **Failure Points** | Drifts back to robotic, safe defaults when forced to stick to tight word-count rules. | Sacrifices strict markdown structural layouts to prioritize a natural, human-sounding conversational voice. |

#### Key Takeaway:
ChatGPT is a structural workhorse—if you need rigid, predictable data tables, it will format them flawlessly, even if the tone is slightly dry. Claude is a creative realist—it will give you incredibly authentic, human-sounding prose, but it will occasionally bend your formatting rules to let its "personality" shine.

---

## The Final Reusable Prompt Template

```markdown
You are a blunt, technical team lead mentoring a junior developer. Your job is to translate bloated, jargon-heavy corporate job descriptions into raw, practical daily tasks. 

Analyze the input text and extract the real work hidden underneath the buzzwords. 

### Instructions:
1. Format your response as a clean Markdown table with two columns: "What they wrote" and "What you actually do".
2. Keep the "What you actually do" translations under 12 words.
3. Avoid all corporate jargon, HR-speak, and generic fluff. Use direct, conversational, and gritty developer terms.

### Example:
- What they wrote: "Utilize cutting-edge paradigm shifts to optimize pipeline throughput."
- What you actually do: "Fix the slow CI/CD build scripts so deployments don't drag."

### Input Job Description to Translate:
[PASTE TEXT HERE]
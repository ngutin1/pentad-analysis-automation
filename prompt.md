You are analyzing campaign speech transcripts using Burke's pentad framework. Your task is to identify and extract specific rhetorical elements, focusing on the RATIOS between Act and Agent.

TASK: Analyze the following speech transcript and return ONLY valid JSON with no additional commentary.

CODING RULES:

ACT (what is being done):
- policy_economic: Any mention of economic policy (jobs, wages, taxes, healthcare costs, housing, unions, Social Security, Medicare, childcare, family leave, middle class)
- policy_social: Social policy (abortion rights, gun control, voting rights, criminal justice, education, civil rights)
- policy_foreign: Foreign policy, military, international relations, immigration/border security
- attack_opp: Characterizing opponent as threat/danger/criminal/incompetent/unfit
- past_actions: References to past accomplishments or actions already taken

AGENT (who is acting):
- self: Kamala Harris as individual ("I", "me", "my")
- admin: Biden-Harris administration ("we" in governing context, "our administration")
- trump: Donald Trump as agent
- billionaires: Wealthy/corporations/Wall Street as agents
- marginalized: Immigrants, LGBTQ people, people of color, women, workers, seniors as agents/subjects

CRITICAL: PENTAD ANALYSIS REQUIRES ACT-AGENT RATIOS
For EACH excerpt you extract, you MUST identify BOTH:
1. Which ACT is being performed
2. Which AGENT is performing that act

EXTRACTION RULES:
1. Extract the MINIMAL phrase that triggers the tag (3-15 words typical)
2. Include enough context to understand the point, but no more
3. EVERY excerpt must have exactly ONE act tag and ONE agent tag
4. Do not paraphrase - extract exact text from transcript
5. Maintain original capitalization and punctuation from source

OUTPUT FORMAT (strict JSON):
{
  "speech_metadata": {
    "date": "YYYY-MM-DD",
    "type": "event_type",
    "location": "location",
    "chunk_id": "id",
    "word_count": number
  },
  "pentad_analysis": {
    "act_frequencies": {
      "policy_economic": 0,
      "policy_social": 0,
      "policy_foreign": 0,
      "attack_opp": 0,
      "past_actions": 0
    },
    "agent_frequencies": {
      "self": 0,
      "admin": 0,
      "trump": 0,
      "billionaires": 0,
      "marginalized": 0
    },
    "ratio_frequencies": {
      "self+policy_economic": 0,
      "self+policy_social": 0,
      "self+policy_foreign": 0,
      "self+attack_opp": 0,
      "self+past_actions": 0,
      "admin+policy_economic": 0,
      "admin+policy_social": 0,
      "admin+policy_foreign": 0,
      "admin+attack_opp": 0,
      "admin+past_actions": 0,
      "trump+policy_economic": 0,
      "trump+policy_social": 0,
      "trump+policy_foreign": 0,
      "trump+attack_opp": 0,
      "trump+past_actions": 0,
      "billionaires+policy_economic": 0,
      "billionaires+policy_social": 0,
      "billionaires+policy_foreign": 0,
      "billionaires+attack_opp": 0,
      "billionaires+past_actions": 0,
      "marginalized+policy_economic": 0,
      "marginalized+policy_social": 0,
      "marginalized+policy_foreign": 0,
      "marginalized+attack_opp": 0,
      "marginalized+past_actions": 0
    }
  },
  "tagged_excerpts": [
    {
      "text": "exact excerpt from transcript",
      "act": "policy_economic",
      "agent": "self"
    },
    {
      "text": "another exact excerpt",
      "act": "attack_opp",
      "agent": "trump"
    }
  ]
}

EXAMPLES OF ACT-AGENT RATIOS:

"building up the middle class will be a defining goal of my presidency"
→ act: policy_economic, agent: self

"Donald Trump intends to cut Social Security and Medicare"
→ act: policy_economic, agent: trump
(Note: This is Trump as agent doing economic policy, NOT attack_opp - it's describing his policy actions)

"Donald Trump was found liable for committing sexual abuse"
→ act: attack_opp, agent: trump
(This is characterizing Trump as a criminal/threat)

"I took on the big Wall Street banks and held them accountable for fraud"
→ act: past_actions, agent: self

"we passed the Inflation Reduction Act"
→ act: past_actions, agent: admin

"give tax breaks to billionaires and big corporations"
→ act: policy_economic, agent: billionaires
(Context: Trump giving them tax breaks, but billionaires are the beneficiary agents)

"women should be punished for their choices"
→ act: attack_opp, agent: trump
(Trump's statement attacking women's autonomy)

"every worker has the freedom to join a union"
→ act: policy_economic, agent: marginalized
(Workers as the subject/agent of the policy)

CRITICAL DISTINCTIONS:

1. **Trump as agent of policy vs attack:**
   - "Trump will cut Social Security" = trump+policy_economic (describing his policy)
   - "Trump is a convicted felon" = trump+attack_opp (characterizing him as threat)

2. **Self vs Admin:**
   - "I will sign it into law" = self+policy_*
   - "We passed the infrastructure bill" = admin+past_actions

3. **Who is the primary agent?**
   - "I will help working families" = self+policy_economic (Kamala is agent helping families)
   - "working families deserve relief" = marginalized+policy_economic (families are the subjects)

CRITICAL REMINDERS:
- Return ONLY the JSON object
- Ensure all JSON is valid (proper quotes, commas, brackets)
- Every excerpt MUST have both act and agent tags
- Frequencies must match: len(tagged_excerpts) = sum of all ratio_frequencies
- act_frequencies should sum up across agents (e.g., all policy_economic regardless of agent)
- agent_frequencies should sum up across acts (e.g., all self regardless of act)

TRANSCRIPT TO ANALYZE:

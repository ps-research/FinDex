# Financial Distress Classification Task

You are an expert annotator tasked with analyzing social media posts about financial distress. Your goal is to identify both the **Intent** (why the person is posting) and **Impact** (what consequences they are experiencing) using a dual taxonomy system.

## Important Guidelines

- **Multi-label classification**: Posts can have MULTIPLE Intent labels and MULTIPLE Impact labels simultaneously
- **Base decisions on evidence**: Only assign labels when there is clear textual evidence
- **Consider implicit signals**: Impacts can be inferred from strong contextual evidence even without explicit statements
- **Return format**: Provide your answer as two JSON lists

## INTENT TAXONOMY (7 Categories)

### 1. Instrumental Help-Seeking
**Definition:** Direct and explicit pursuit of tangible aid, financial assistance, material goods, or specific services to alleviate an immediate financial shortfall.

**Key Indicators:**
- Sharing crowdfunding links (GoFundMe, etc.)
- Directly asking for money or donations ("Can anyone help with my rent/medical bill?")
- Posting payment app handles (Venmo, Cash App, PayPal)
- Requesting specific goods or services ("Does anyone have a spare car seat?")

### 2. Informational Help-Seeking
**Definition:** Active pursuit of knowledge, advice, guidance, or recommendations to understand a complex financial topic, navigate a system, or solve a problem.

**Key Indicators:**
- Posing direct questions ("How do I start consolidating my debt?")
- Seeking recommendations ("What's the best app for budgeting?")
- Asking for clarification on financial concepts ("Can someone explain the difference between a Roth and traditional IRA?")
- Soliciting opinions on a course of action ("Should I use my savings to pay off my credit card?")

### 3. Emotional & Esteem Support-Seeking
**Definition:** Sharing personal feelings and struggles with the primary goal of receiving emotional comfort, empathy, validation, and encouragement.

**Key Indicators:**
- Expressions of vulnerability and negative affect ("Feeling so defeated by my student loans")
- Seeking validation ("Am I the only one who feels like they're drowning?")
- Statements explicitly requesting emotional connection ("Just needed to share this with people who get it")
- Use of language related to shame, fear, or hopelessness

### 4. Venting / Catharsis
**Definition:** Unstructured, often intense expression of raw negative emotions such as frustration, anger, despair, or anxiety related to a financial situation.

**Key Indicators:**
- Use of profanity, expletives, and emotionally charged language
- Capitalized text for emphasis ("I HATE THIS")
- Expressions of hopelessness and powerlessness ("I can't take it anymore," "It's all so unfair")
- Rhetorical questions not seeking an answer ("Why does this always happen to me?")

### 5. Community Building & Solidarity Seeking
**Definition:** Posts intended to find, connect with, and affiliate with a group of peers who share similar financial challenges.

**Key Indicators:**
- Using "calling all..." phrases ("Calling all single parents struggling with debt")
- Creating or using community-specific hashtags (#debtfreecommunity)
- Posts seeking to affirm a shared experience ("Who else is dealing with insane student loan payments?")
- Organizing or suggesting formation of support groups

### 6. Sense-Making & Narrative Construction
**Definition:** The cognitive process of articulating one's financial experiences into a coherent story or narrative to process, understand, and gain a sense of control over the situation.

**Key Indicators:**
- Longer, detailed posts that recount a sequence of events
- Use of temporal markers ("It all started when...", "Then, last year...", "Looking back, I see now...")
- Reflective or analytical language ("I realize now that my biggest mistake was...")
- Attempts to draw lessons or morals from the experience

### 7. Advocacy & Warning
**Definition:** Sharing a negative personal experience with a financial product, service, or institution with the explicit goal of warning other consumers or advocating for systemic change.

**Key Indicators:**
- Explicitly naming companies, products, or services
- Using strong warning language ("Warning: Do NOT use [Company Name]," "BEWARE of this scam")
- Detailing specific mechanisms of a predatory practice or fraud
- Encouraging others to file complaints or take collective action

---

## IMPACT TAXONOMY (6 Categories)

### 1. Psychological & Emotional Impact
**Definition:** The manifestation of adverse effects on an individual's mental health and emotional state, including heightened anxiety, symptoms of depression, feelings of hopelessness, shame, fear, anger, and diminished self-esteem.

**Key Indicators:**
- Direct mentions of mental health conditions ("My depression is so much worse when I think about my debt")
- Expressions of pervasive worry, fear, or anxiety ("I'm so anxious I can't sleep")
- Statements reflecting low self-worth or shame ("This debt makes me feel like a failure")
- Expressions of hopelessness or despair ("I don't see a way out")

### 2. Cognitive Impact
**Definition:** The impairment of cognitive functions, including concentration, memory, planning, problem-solving, and decision-making capacity, due to the overwhelming mental burden and stress of financial scarcity.

**Key Indicators:**
- Expressions of feeling overwhelmed or paralyzed ("I'm so overwhelmed I can't even figure out where to start")
- Statements about inability to focus or think clearly ("My brain feels foggy every time I try to look at my bills")
- Descriptions of confusion and indecisiveness ("I know I need to do something, but I can't decide what")
- Self-reported difficulty in completing complex financial tasks

### 3. Physical Health Impact
**Definition:** The emergence or exacerbation of stress-related physical symptoms, or the inability to access or afford necessary medical care, medication, or healthy lifestyle choices.

**Key Indicators:**
- Direct mentions of physical symptoms linked to stress ("Haven't slept in weeks worrying about money")
- Statements about forgoing medical care ("Had to cancel my doctor's appointment because I can't afford the co-pay")
- Descriptions of being unable to afford prescriptions or treatment ("Choosing between my medication and my electric bill")

### 4. Relational & Social Impact
**Definition:** The negative effects of financial problems on interpersonal relationships with partners, family, and friends, as well as withdrawal from social activities.

**Key Indicators:**
- Descriptions of arguments with a partner or family about money ("My spouse and I fight about money constantly")
- Expressions of social isolation ("Had to cancel on my friends again because I'm broke")
- Statements about feeling disconnected or alone ("Feeling so alone in this struggle")
- Mentioning the strain that financial issues are putting on family dynamics

### 5. Behavioral Impact (Maladaptive Coping)
**Definition:** The adoption of unhealthy or counterproductive behaviors as a means of escaping, avoiding, or managing the emotional pain of financial stress.

**Key Indicators:**
- Confessions of impulsive or emotional spending ("Just spent my rent money on a shopping spree to feel better")
- References to substance use as an escape ("Drinking is the only way I can stop worrying about my debt")
- Mentions of gambling
- Descriptions of avoidance ("I'm too scared to even open my bank app or look at my bills")

### 6. Economic & Material Impact
**Definition:** The direct, observable, and tangible consequences of financial distress, including unmanageable debt, depletion of savings, loss of income, or inability to afford basic necessities.

**Key Indicators:**
- Specific mentions of debt ("Maxed out another credit card," "My student loans are crushing me")
- Descriptions of depleting assets ("Had to cash out my 401k," "Had to sell my car to make rent")
- Statements about income loss ("Just got laid off," "My hours were cut again")
- Descriptions of struggling to afford essentials ("Choosing between groceries and the electric bill," "Facing eviction")

---

## Classification Instructions

1. **Read the post carefully** and identify all applicable Intent and Impact labels
2. **Consider the primary communicative goal** for Intent (what is the person trying to achieve by posting?)
3. **Look for evidence of consequences** for Impact (what negative effects are they experiencing?)
4. **Assign multiple labels** when appropriate - most posts will have 2-4 Intent labels and 2-4 Impact labels
5. **Use exact label names** as specified above

## Output Format

**YOU MUST OUTPUT ONLY VALID JSON IN THE EXACT FORMAT SPECIFIED BELOW. ANY DEVIATION WILL BE CONSIDERED A FAILED ANNOTATION.**

```
{
  "labels": {
    "intent_labels": ["Label1", "Label2", ...],
    "impact_labels": ["Label1", "Label2", ...]
  }
}
```
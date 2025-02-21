# Token counts
Chosen Input prompt:

> You will be sent a MCQ question in a JSON format. Treat the question standalone, i.e. assume that the person trying to answer the question has no special-field knowledge outside the context of the question. 
>
> 
> The premise of this problem is that the question might be broken (not have enough relevant information to be answerable within reasonable standards) or incomplete (might refer to a paragraph/essay/content which is nowhere in the context of the question or its options. 
>
> Your job, as a question-embellisher, is to rewrite the question and/or options of the question, if necessary to make it more "standalone".
> 
> Reply in the following JSON format: 
> {"question": Your possibly embellished question goes here, 
> "options": This will be a list of the options which you may or may not feel the need to change, 
> "answer": The correct one out of the options (only change if necesary to keep context), 
> "changed": Boolean. Put this to True if you changed anything, and False if you didn't change anything about the input question, 
> "standalone": Boolean. This should be true if YOU determine that this question makes sense standalone. False, if not. Be extra strict about this, please mark questions as False if you AT ALL think that it doesn't make sense on its own, and/or is incomplete to be answerable}  
> The question to embellish is:

 **Input tokens from the prompt:** 

According to https://token-calculator.net/ : **282 tokens**

According to Gemini tokenizer: **294 tokens**

According to [Claude 3.5 Sonnet token counter (third-party)](https://token-counter.app/anthropic/claude-3.5-sonnet): **297 tokens**

According to [Deepseek-V3 token-counter (third-party)](https://reemix.co/tools/deepseek-v3-token-counter): **282 tokens**


---

### Sample Question in Input prompt:
> {"question":  "In interviews, despots are often surprisingly ___________; this helps to explain how seemingly awful people are able to command so many followers.",  "options": ["malign",  "indignant",  "forgiving",  "personable",  "munificent"],  "answer":  "personable"}

**Average (of 10 questions of varying length) tokens count of prompt questions**:

According to https://token-calculator.net/: **221 tokens**

According to Gemini tokenizer: **218.5 tokens**

According to [Claude 3.5 Sonnet token counter (third-party)](https://token-counter.app/anthropic/claude-3.5-sonnet): **220.5 tokens**

According to [Deepseek-V3 token-counter (third-party)](https://reemix.co/tools/deepseek-v3-token-counter): **207.5 tokens**


**Total of input tokens for each model**:
1. Gemini 2.0 Flash: 294 + 218.5 = 512.5
2. Claude 3.5 Sonnet: 297 + 220.5 = 517.5
3. Deepseek-chat-V3: 282 + 207.5 = 489.5

---

#### Sample Output:

> { "question": "This appears to be a pattern recognition question with
> an image containing rows of numbered items, where a question mark
> needs to be replaced with a number to complete the pattern. However,
> since no image is provided, this question cannot be properly posed or
> answered.", "options": ["(a) 3", "(b) 6", "(c) 2", "(d) 5"], "answer":
> "(d) 5", "changed": true, "standalone": false }

**Average (of 10 prompts questions of varying length) Output token of each model**:

1. Gemini 2.0 Flash: **193 tokens**
2. Claude 3.5 Sonnet: **198 tokens**
3. Deepseek-chat-V3: **187 tokens**

---
**Cost of each of these models (PER QUESTION):**

**Gemini 2.0 Flash:**
1. cost per input token = $0.10/1,000,000 = $0.0000001
2. cost per output token = unmentioned on the official website so assuming its the same as input token

> Our calculation = (Input tokens + Output Tokens)* $0.0000001 = (512.5 + 193)* 0.0000001 = **$0.00007055**

**Claude 3.5 Sonnet:**
1. cost per input token = $3/1,000,000 = $0.000003
2. cost per output token = $15/1,000,000 = 0.000015

> Our calculation = (Input  tokens * $0.000003) + (Output tokens * $0.000015) = (517.5 * 0.000003) + (198 *0.000015) = 0.0015525 + 0.00297 = **$0.0045225**

**Deepseek-chat-V3**
1. cost per input token = $0.07/1,000,000 = $0.00000007
2. cost per output token = $1.10/1,000,000 = $0.0000011

> Our calculation = (Input  tokens * $0.00000007) + (Output tokens * $0.0000011) = (489.5 * $0.00000007) + (187 * $0.0000011) = 0.000034265 + 0.0002057 = **$0.000239965**

---

### Prices table:

|MODELS                |AVG INPUT TOKENS                       | AVG OUTPUT TOKENS  |  AVG COST|          RATING (for this job)       |
|----------------|-------------------------------|-----------------------------|------------|------------
|Gemini 2.0 Flash|          512.5            |193| $0.00007055|WORST
|Claude 3.5 Sonnet     |517.5            |   198         | $0.0045225|BEST
|Deepseek-chat-V3   |489.5|187| $0.000239965| GOOD

---



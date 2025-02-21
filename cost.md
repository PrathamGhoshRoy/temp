# Cost Analysis

Input prompt:

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

According to [ChatGPT Official Tokenizer](https://platform.openai.com/tokenizer): **272 tokens**

---

### Sample Question in Input prompt (Just to get an idea):
> {"question":  "In interviews, despots are often surprisingly ___________; this helps to explain how seemingly awful people are able to command so many followers.",  "options": ["malign",  "indignant",  "forgiving",  "personable",  "munificent"],  "answer":  "personable"}
---
**Average (of 10 questions of varying length) tokens count of prompt questions**:

According to https://token-calculator.net/: **221 tokens**

According to Gemini tokenizer: **218.5 tokens**

According to [Claude 3.5 Sonnet token counter (third-party)](https://token-counter.app/anthropic/claude-3.5-sonnet): **220.5 tokens**

According to [Deepseek-V3 token-counter (third-party)](https://reemix.co/tools/deepseek-v3-token-counter): **207.5 tokens**

According to [ChatGPT Official Tokenizer](https://platform.openai.com/tokenizer): **198 tokens**

---

**Total of input tokens for each model**:

Gemini 2.0 Flash: 294 + 218.5 = 512.5

Gemini 1.5 Pro: 294 + 218.5 = 512.5

Claude 3.5 Sonnet: 297 + 220.5 = 517.5

Deepseek-chat-V3: 282 + 207.5 = 489.5

GPT 4o-mini: 272 + 198 = 470

---

#### Sample Output:

> { "question": "This appears to be a pattern recognition question with
> an image containing rows of numbered items, where a question mark
> needs to be replaced with a number to complete the pattern. However,
> since no image is provided, this question cannot be properly posed or
> answered.", "options": ["(a) 3", "(b) 6", "(c) 2", "(d) 5"], "answer":
> "(d) 5", "changed": true, "standalone": false }

---

**Average (of 10 prompts questions of varying length) Output token of each model**:

Gemini 2.0 Flash: **193 tokens**

Gemini 1.5 Pro: **193 tokens**

Claude 3.5 Sonnet: **198 tokens**

Deepseek-chat-V3: **187 tokens**

GPT 4o-mini: **182 tokens**

---

**Gemini 2.0 Flash Cost:**
1. cost per input token = $0.10/1,000,000 = $0.0000001
2. cost per output token =  $0.40/1,000,000 = $0.0000004

> Our calculation = (Input tokens + Output Tokens)* $0.0000001 = (512.5* 0.0000001) + (193 *  0.0000004) =  0.00005125 + 0.0000772 = **$0.00012845**

3. cost per question = $0.00012845
---

**Gemini 1.5 Pro Cost:**
1. cost per input token = $1.25/1,000,000 = $0.00000125
2. cost per output token = $5.00/1,000,000 = $0.000005
> Our calculation = (Input tokens + Output Tokens)* $0.0000001 = (512.5* 0.00000125) + (193*0.000005) = 0.000640625 + 0.000965 = **$0.001605625**

3. cost per question = $0.001605625
---


**Claude 3.5 Sonnet Cost:**
1. cost per input token = $3/1,000,000 = $0.000003
2. cost per output token = $15/1,000,000 = 0.000015

> Our calculation = (Input  tokens * $0.000003) + (Output tokens * $0.000015) = (517.5 * 0.000003) + (198 *0.000015) = 0.0015525 + 0.00297 = **$0.0045225**
3. cost per question = $0.0045225
---

**Deepseek-chat-V3 Cost:**
1. cost per input token = $0.07/1,000,000 = $0.00000007
2. cost per output token = $1.10/1,000,000 = $0.0000011

> Our calculation = (Input  tokens * $0.00000007) + (Output tokens * $0.0000011) = (489.5 * $0.00000007) + (187 * $0.0000011) = 0.000034265 + 0.0002057 = **$0.000239965**
3. cost per question = $0.000239965
---
**GPT 4o-mini Cost:**
1. cost per input token = $0.150/1,000,000 = $0.00000015
2. cost per output token = $0.600/1,000,000 = $0.0000006

> Our calculation = (Input  tokens * $0.00000015) + (Output tokens * $0.0000006) = (470 * 0.00000015) + (182 * 0.0000006) = (0.0000705 + 0.0001092) = **$0.0001797**
3. cost per question = $0.0001797
---
**Cost for our dataset i.e. ~ 5.8k questions:**
1. Gemini 2.0 Flash= ($0.00007055 * 5793) = $0.40869615
2. Gemini 1.5 Pro = ($0.001605625 * 5793) = $9.301385625
3. Claude 3.5 Sonnet = ($0.0045225 * 5793) = $26.1988425
4. Deepseek-chat-V3 = ($0.000239965 * 5793) = $1.390117245
5. GPT 4o-mini = ($0.0001797 * 5793) = $1.0410021
---


|MODELS                |AVG INPUT TOKENS                       | AVG OUTPUT TOKENS  |  ESTIMATED COST PER QUESTION|ESTIMATE COST FOR OUR DATASET |         RATING (for this job)       |
|----------------|-------------------------------|-----------------------------|------------|------------|------
|Gemini 2.0 Flash|          512.5            |193| $0.00007055|$0.40869615|Bad
|Gemini 1.5 Pro| 512.5|193| $0.001605625|$9.301385625|Good, on par with Deepseek
|Claude 3.5 Sonnet     |517.5            |   198         | $0.0045225|$26.1988425|Best
|Deepseek-chat-V3   |489.5|187| $0.000239965|$1.390117245| Good
|GPT 4o-mini|470|182| $0.0001797|$1.0410021|Good, better than deepseek at rephrasing while keeping context



# EX-02-Cross-Platform-Prompting-Evaluating-Diverse-Techniques-in-AI-Powered-Text-Summarization

## AIM
To evaluate and compare the effectiveness of prompting techniques (zero-shot, few-shot, chain-of-thought, role-based) across different AI platforms (e.g., ChatGPT, Gemini, Claude, Copilot) in a specific task: text summarization.

## Scenario:
You are part of a content curation team for an educational platform that delivers quick summaries of research papers to undergraduate students. Your task is to summarize a 500-word technical article on "The Basics of Blockchain Technology" using multiple AI platforms and prompting strategies.

Your goal is to determine which combination of prompting technique + platform provides the best summary in terms of:

Accuracy

Coherence

Simplicity

Speed

User experience

## Algorithm
# Evaluation and Comparison of Prompting Techniques for Text Summarization
## 1. Prompting Techniques in Detail
### Zero-Shot Prompting

Zero-shot prompting refers to giving an AI model a direct instruction without any examples of how the output should look. In text summarization, this usually means asking the model to “summarize the following article” with a length or style constraint. This method leverages the model’s pretraining on massive amounts of text, where it has already encountered summarization-like tasks indirectly. For example, a zero-shot prompt could simply be: “Summarize the following research abstract in three sentences, keeping the technical accuracy intact.”

The strength of zero-shot prompting lies in its simplicity and efficiency. It requires no additional design effort or space in the prompt, making it ideal for quick tasks or when token budget is limited. Zero-shot also reveals the raw capability of the model — it shows how well the model can generalize summarization without explicit guidance. For models like ChatGPT and Claude, zero-shot often produces coherent, concise summaries that capture the main ideas with minimal hallucination.

However, there are also weaknesses. Zero-shot outputs can vary widely in style depending on the platform. For example, one model may produce a news-style summary while another may write an academic-like abstract, even for the same text. There is also less control over specific aspects such as tone, level of detail, or adherence to sentence limits. In some cases, especially with weaker models like Copilot, the summary may miss important details or oversimplify the content. Thus, while zero-shot is fast and practical, it is not always reliable when high accuracy or specific formatting is required.

### Few-Shot Prompting

Few-shot prompting provides the model with a set of example inputs and outputs before asking it to generate the target summary. In text summarization, this involves showing the model two or three short passages with their ideal summaries and then giving it the actual text to summarize. For example:

Example 1: A news paragraph → a concise 2-sentence news summary.

Example 2: A research abstract → a short technical summary.

Example 3: A story excerpt → a narrative-style summary.

After these demonstrations, the model is asked: “Now summarize the following article in 3 sentences.”

This technique strongly guides the model toward a desired style, format, and level of conciseness. By showing examples, we reduce ambiguity in what is expected, and the model imitates the patterns provided. Few-shot prompting is particularly effective for aligning summaries to specific audiences, such as producing simplified summaries for children or detailed ones for professionals. On platforms like ChatGPT and Claude, few-shot often yields the highest-quality summaries that are both concise and faithful. Gemini also benefits, especially in avoiding vague phrasing, while Copilot shows moderate improvement compared to its zero-shot output.

The limitation is that few-shot prompts consume more tokens, which increases cost and may exceed prompt length limits for very large examples. The technique also requires effort to prepare good examples. Poorly chosen or inconsistent examples can confuse the model and reduce quality. Nevertheless, when carefully designed, few-shot prompting offers one of the most reliable ways to improve summarization performance across platforms.

### Chain-of-Thought (CoT) Prompting

Chain-of-Thought prompting encourages the model to generate reasoning steps before providing the final answer. In summarization, this often means asking the model to first identify the key points in the text, list them as bullets, and then write a concise summary. For example:

Step 1: List the 5 main events or findings.

Step 2: Use these points to form a 3–4 sentence summary.

This process mimics how a human might first highlight important information and then condense it. CoT prompting improves coverage and factual accuracy, especially for long or complex texts such as research papers, legal documents, or multi-event news reports. By explicitly breaking down reasoning, the model is less likely to omit critical points. Platforms like ChatGPT and Claude handle this very well, often producing summaries that capture nuances better than zero-shot or few-shot.

The main drawback is verbosity. Since the model is instructed to “think step by step,” it often outputs both the reasoning process and the summary, which can be unnecessarily long. This may not suit applications where only a clean summary is required. Additionally, weaker platforms like Copilot struggle with CoT, often skipping the reasoning or failing to compress it properly. In practice, CoT is most useful when faithfulness and coverage are more important than brevity, such as in academic or technical summarization.

### Role-Based Prompting

Role-based prompting assigns a persona or role to the AI, which shapes the style and focus of the summary. For example: “You are a professional news editor. Summarize this article for the public in three sentences.” or “You are a science communicator. Summarize this research paper in simple terms for high school students.”

This method is highly effective for tailoring summaries to specific audiences. It not only controls tone and style but also prioritizes information differently depending on the role. For instance, a news editor persona will emphasize “what happened” and “why it matters,” while a scientist persona may focus on methodology and results. Platforms like Claude and ChatGPT excel at following roles closely, producing summaries that align with the assigned persona. Gemini performs reasonably well but may sometimes stick rigidly to instructions, while Copilot often ignores the role and generates plain summaries.

The main limitation of role-based prompting is that style control sometimes comes at the cost of completeness. For example, an executive summary might leave out technical details, which could be important in some contexts. Additionally, if the role is too vague or unrealistic, the model may produce inconsistent results. Despite this, role-based prompting is highly practical for real-world applications where summaries must be audience-specific, such as journalism, education, or business reporting.

## 2. Comparison Table — Effectiveness Across Platforms

| **Technique**        | **ChatGPT**                                            | **Gemini**                              | **Claude**                                               | **Copilot**                                             |
| -------------------- | ------------------------------------------------------ | --------------------------------------- | -------------------------------------------------------- | ------------------------------------------------------- |
| **Zero-Shot**        | High quality, concise; reliable for short/medium texts | Good summaries, but sometimes vague     | Accurate but occasionally wordy                          | Limited; summaries often short, less nuanced            |
| **Few-Shot**         | Very effective; strong format/style adherence          | Improves clarity and conciseness        | Consistently strong, close to ChatGPT                    | Moderate improvement, still weaker than others          |
| **Chain-of-Thought** | Great for complex texts; high factual coverage         | Good coverage, but can become verbose   | Strong logical breakdown; high fidelity                  | Weak, tends to output plain summaries without reasoning |
| **Role-Based**       | Excellent tone control (news/editor/scientist)         | Good persona following, sometimes rigid | Very strong persona alignment; best for styled summaries | Limited persona control, often ignores role             |

## 3. Key Insights in Detail

The comparative study of prompting techniques across multiple AI platforms highlights several important insights about how prompts shape summarization quality.

First, zero-shot prompting demonstrates the raw summarization ability of each model. ChatGPT and Claude show strong performance even without examples, often producing fluent and accurate summaries. Gemini tends to be slightly less precise, sometimes generating vague or generic summaries, while Copilot consistently underperforms due to its coding-oriented training. This confirms that zero-shot is only as good as the model’s inherent alignment with summarization tasks.

Second, few-shot prompting consistently improves results across all platforms. By providing examples, the models align more closely with the desired style, level of conciseness, and formatting. This effect is strongest for ChatGPT and Claude, which already perform well and improve further with guidance. Gemini also benefits noticeably, reducing vagueness and producing clearer summaries. Even Copilot, although weaker overall, shows improvement with few-shot examples. This highlights the importance of demonstration in prompt engineering.

Third, chain-of-thought prompting reveals a trade-off between faithfulness and conciseness. For complex texts, CoT helps models capture more details accurately, especially in platforms like Claude, which excels at structured reasoning. However, the method also tends to produce longer outputs, which may not suit scenarios requiring brevity. Gemini shows similar strengths but can become overly verbose, while Copilot struggles to follow reasoning steps. Thus, CoT is best used when coverage is prioritized over length, such as in academic or legal summarization.

Finally, role-based prompting emerges as the most powerful tool for tailoring summaries to different audiences. Assigning roles such as “news editor,” “science communicator,” or “executive advisor” allows the model to adjust tone, terminology, and focus. Claude demonstrates the strongest persona alignment, reliably adopting the requested role. ChatGPT also performs very well, balancing style and accuracy effectively. Gemini follows roles reasonably but sometimes rigidly, while Copilot often ignores the role instructions. This makes role-based prompting highly valuable in professional settings where summaries must be adapted to specific readers.

In conclusion, the study shows that few-shot and role-based prompting deliver the best overall performance, improving clarity, conciseness, and style alignment across platforms. Chain-of-thought is highly effective for ensuring factual coverage in complex texts but may reduce conciseness. Zero-shot works well with advanced models but is less reliable for weaker ones. The choice of technique should therefore depend on the platform being used, the complexity of the text, and the intended audience of the summary.
## Graphical comparison

<img width="891" height="539" alt="image" src="https://github.com/user-attachments/assets/ab3076ee-7e2b-4cda-a85c-ab88e2741e45" />


## Result

The evaluation shows that prompting techniques significantly affect summarization quality across AI platforms. Zero-shot is quick but inconsistent, especially on weaker models like Copilot. Few-shot provides the best balance of clarity and style by guiding the model with examples. Chain-of-thought improves factual accuracy in complex texts but often produces longer outputs. Role-based prompting excels at tailoring tone and focus to specific audiences, with Claude and ChatGPT handling roles most effectively. Overall, few-shot and role-based prompting deliver the strongest results for practical summarization tasks.


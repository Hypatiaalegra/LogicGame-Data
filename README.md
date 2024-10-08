# LogicGame-Data
Dev and Whole Data of LogicGame benchmark. [Paper Arxiv](https://arxiv.org/abs/2408.15778)

## Introduction
We introduce benchmark ___LogicGame___, designed to evaluate the logic rule understanding, execution, and planning capabilities of Large Language Models (LLMs). ___LogicGame___ features diverse games with predefined regulations, specifically created to assess logical reasoning independent of mere knowledge. The benchmark tests models across various difficulty levels, aiming for a comprehensive evaluation of performance on rule-based reasoning and multi-step execution and planning.

## Data Description
This project is a benchmark data release that includes four `.jsonl` files: `en_dev`, `zh_dev`, `en_all`, and `zh_all`. These files represent the English and Chinese versions of the development (dev) and complete sets (whole sets), respectively. Each language version corresponds directly with its counterpart. The dev sets contain 10 entries each, whereas the whole sets contain 304 entries each.

The `zh_all` and `en_all` files are used as input data for [Our Codabench Submission](https://www.codabench.org/competitions/4140/) where you can utilize the **contexts** provided in these files as prompts to obtain model responses for evaluation. The dev set is primarily for detailed demonstration purposes.

### Dev Dataset Fields:
- **qid**: A unique identifier for the data entry.
- **contexts**: The benchmark question, which is a combination of rules, question, and output constraints.
- **reference**: The reference JSON answer and process.
- **level**: The difficulty level, with levels ranging from 0 to 3.
- **examples**: Few-shot examples.
- **category**: The type/category of the data.

### Whole(_all) Dataset Fields: 
- **qid**: A unique identifier for the data entry.
- **contexts**: The benchmark question.
- **level**: The difficulty level of the question.
- **category**: The category/task of the data.

## Leaderboard
The definition of metrics in both Tables can be found in the Paper. The best performance is marked in **bold**.
### Performance of 14 models on LogicGame of **zh** version
| Model              | AP-Acc% | A-Acc% | P-Acc% | IFError% | JSError% |
|--------------------|---------|--------|--------|----------|----------|
| o1-preview         | **54.93**   | **67.11**  | **66.85**  | **0.00**     | **0.00**     |
| o1-mini            | 51.97   | 63.49  | 64.97  | **0.00**     | **0.00**     |
| claude-3-5-sonnet  | 30.26   | 39.47  | 43.20  | **0.00**     | **0.00**     |
| gpt-4o             | 26.97   | 35.86  | 39.25  | 0.33     | **0.00**     |
| gpt-4-turbo-0409   | 25.66   | 32.24  | 38.18  | 0.99     | 0.66     |
| glm-4-plus         | 21.71   | 28.29  | 32.76  | 9.21     | 0.33     |
| qwen2-72b          | 20.39   | 27.96  | 32.61  | 2.63     | 0.99     |
| llama-3-70b        | 12.50   | 19.41  | 21.62  | 13.16    | 0.33     |
| claude-3-haiku     | 9.54    | 14.80  | 16.82  | 2.63     | 0.33     |
| glm-4-9b           | 7.57    | 12.83  | 11.27  | 20.39    | 0.99     |
| internlm2-5-7b     | 4.61    | 7.24   | 9.81   | 11.18    | 3.29     |
| llama-3-8b         | 3.62    | 5.26   | 9.31   | 35.53    | **0.00**    |
| mistral-7b         | 2.96    | 3.95   | 6.63   | 26.32    | 6.25     |
| qwen2-7b           | 2.63    | 4.61   | 7.32   | 3.29     | 2.96     |



<!-- | **Model**    | **Execution**    |    |    |    | **Avg.**    | **Planning**    |    |    |    | **Avg.**    | **Overall**    |
|--------------|----------------------|-----|-----|-----|----------------------|--------------------|-----|-----|-----|--------------------|-------------------|
|              | **Level 0** | **Level 1** | **Level 2** | **Level 3** |                  | **Level 0** | **Level 1** | **Level 2** | **Level 3** |                    |                    |
| **o1-preview** | **82.22** | **66.67** | **48.89** | **42.22** | **60.00** | **64.52** | **58.06** | **35.48** | **32.26** | **47.58** | **54.93** |
| **o1-mini** | 77.78 | 57.78 | **48.89** | **42.22** | 56.67 | 74.19 | **58.06** | **35.48** | 12.90 | 45.16 | 51.97 |
| **claude-3-5-sonnet** | 68.89 | 40.00 | 22.22 | 15.56 | 36.67 | 48.39 | 25.81 | 6.45 | 3.23 | 20.97 | 30.26 |
| **gpt-4o** | 62.22 | 31.11 | 13.33 | 13.33 | 30.00 | 51.61 | 22.58 | 9.68 | 6.45 | 22.58 | 26.97 |
| **gpt-4-turbo-0409** | 60.00 | 15.56 | 15.56 | 11.11 | 25.56 | 67.74 | 22.58 | 9.68 | 3.23 | 25.81 | 25.66 |
| **glm-4-plus** | 42.22 | 26.67 | 17.78 | 6.67 | 23.33 | 48.39 | 19.35 | 6.45 | 3.23 | 19.36 | 21.71 |
| **qwen2-72b** | 53.33 | 20.00 | 15.56 | 2.22 | 22.78 | 45.16 | 16.13 | 3.23 | 3.23 | 16.94 | 20.39 |
| **llama-3-70b** | 42.22 | 11.11 | 6.67 | 2.22 | 15.56 | 25.81 | 6.45 | 0.00 | 0.00 | 8.07 | 12.50 |
| **claude-3-haiku** | 31.11 | 4.44 | 2.22 | 0.00 | 9.44 | 32.26 | 6.45 | 0.00 | 0.00 | 9.68 | 9.54 |
| **glm-4-9b** | 24.44 | 8.89 | 2.22 | 0.00 | 8.89 | 19.35 | 3.23 | 0.00 | 0.00 | 5.65 | 7.57 |
| **internlm2-5-7b** | 13.33 | 4.44 | 0.00 | 0.00 | 4.44 | 16.13 | 3.23 | 0.00 | 0.00 | 4.84 | 4.61 |
| **llama-3-8b** | 11.11 | 2.22 | 0.00 | 0.00 | 3.33 | 9.68 | 6.45 | 0.00 | 0.00 | 4.03 | 3.62 |
| **mistral-7b** | 4.44 | 0.00 | 0.00 | 0.00 | 1.11 | 19.35 | 3.23 | 0.00 | 0.00 | 5.65 | 2.96 |
| **qwen2-7b** | 4.44 | 0.00 | 0.00 | 0.00 | 1.11 | 16.13 | 3.23 | 0.00 | 0.00 | 4.84 | 2.63 | -->

### Performance of 14 models on LogicGame of **en** version
| Model              | AP-Acc% | A-Acc% | P-Acc% | IFError% | JSError% |
|--------------------|---------|--------|--------|----------|----------|
| o1-preview         | **53.29**   | **65.46**  | **64.82**  | 0.33     | **0.00**     |
| o1-mini            | 49.67   | 61.18  | 63.25  | 0.66     | 0.33     |
| claude-3-5-sonnet  | 29.28   | 37.17  | 43.48  | 0.33     | **0.00**    |
| gpt-4o             | 28.29   | 41.12  | 42.43  | 0.66     | 0.66     |
| gpt-4-turbo-0409   | 21.05   | 28.95  | 33.83  | 0.66     | 0.99     |
| glm-4-plus         | 17.76   | 24.34  | 28.36  | 6.91     | 0.66     |
| qwen2-72b          | 8.88    | 13.82  | 18.56  | 24.67    | 0.66     |
| glm-4-9b           | 7.89    | 9.87   | 13.05  | 17.11    | 1.64     |
| internlm2-5-7b     | 6.25    | 7.89   | 13.06  | 13.16    | 1.32     |
| claude-3-haiku     | 4.93    | 8.55   | 12.60  | **0.00**     | 1.64     |
| llama-3-70b        | 4.61    | 8.55   | 11.44  | 55.59    | 0.33     |
| mistral-7b         | 4.28    | 5.26   | 6.95   | 17.43    | 8.88     |
| qwen2-7b           | 1.64    | 3.95   | 5.56   | 1.64     | 8.22     |
| llama-3-8b         | 0.00    | 1.64   | 2.85   | 68.42    | 0.33     |

<!-- | **Model**    | **Execution**    |    |    |    | **Avg.**    | **Planning**    |    |    |    | **Avg.**    | **Overall**    |
|--------------|----------------------|-----|-----|-----|----------------------|--------------------|-----|-----|-----|--------------------|-------------------|
|              | **Level 0** | **Level 1** | **Level 2** | **Level 3** |                  | **Level 0** | **Level 1** | **Level 2** | **Level 3** |                    |                    |
| **o1-preview** | 71.11 | **57.78** | **48.89** | **51.11** | **57.22** | **70.97** | **54.84** | **41.94** | **22.58** | **47.58** | **53.29** |
| **o1-mini** | **73.33** | 46.67 | 44.44 | 46.67 | 52.78 | **70.97** | 48.39 | 38.71 | **22.58** | 45.16 | 49.67 |
| **claude-3-5-sonnet** | 46.67 | 40.00 | 33.33 | 13.33 | 33.33 | 64.52 | 16.13 | 6.45 | 6.45 | 23.39 | 29.28 |
| **gpt-4o** | 57.78 | 37.78 | 31.11 | 13.33 | 35.00 | 48.39 | 19.35 | 3.23 | 3.23 | 18.55 | 28.29 |
| **gpt-4-turbo-0409** | 42.22 | 20.00 | 17.78 | 8.89 | 22.22 | 51.61 | 12.90 | 9.68 | 3.23 | 19.36 | 21.05 |
| **glm-4-plus** | 31.11 | 15.56 | 17.78 | 6.67 | 17.78 | 48.39 | 9.68 | 9.68 | 3.23 | 17.75 | 17.76 |
| **qwen2-72b** | 28.89 | 4.44 | 0.00 | 0.00 | 8.33 | 22.58 | 6.45 | 6.45 | 3.23 | 9.68 | 8.88 |
| **glm-4-9b** | 22.22 | 6.67 | 2.22 | 2.22 | 8.33 | 22.58 | 6.45 | 0.00 | 0.00 | 7.26 | 7.89 |
| **internlm2-5-7b** | 22.22 | 4.44 | 4.44 | 0.00 | 7.78 | 12.90 | 3.23 | 0.00 | 0.00 | 4.03 | 6.25 |
| **claude-3-haiku** | 8.89 | 8.89 | 0.00 | 0.00 | 4.45 | 22.58 | 0.00 | 0.00 | 0.00 | 5.65 | 4.93 |
| **llama-3-70b** | 8.89 | 8.89 | 8.89 | 0.00 | 6.67 | 3.23 | 3.23 | 0.00 | 0.00 | 1.62 | 4.61 |
| **mistral-7b** | 22.22 | 0.00 | 0.00 | 0.00 | 5.56 | 9.68 | 0.00 | 0.00 | 0.00 | 2.42 | 4.28 |
| **qwen2-7b** | 4.44 | 2.22 | 0.00 | 0.00 | 1.67 | 6.45 | 0.00 | 0.00 | 0.00 | 1.61 | 1.64 |
| **llama-3-8b** | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 |
 -->

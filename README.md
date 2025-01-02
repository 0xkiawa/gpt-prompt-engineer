# gpt-prompt-engineer
[![Twitter Follow](https://img.shields.io/twitter/follow/mattshumer_?style=social)](https://twitter.com/mattshumer_) [![Open Main Version In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mshumer/gpt-prompt-engineer/blob/main/gpt_prompt_engineer.ipynb) [![Open Classification Version In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/16NLMjqyuUWxcokE_NF6RwHD8grwEeoaJ?usp=sharing)

## Overview

Prompt engineering is kind of like alchemy. There's no clear way to predict what will work best. It's all about experimenting until you find the right prompt. `gpt-prompt-engineer` is a tool that takes this experimentation to a whole new level.

**Simply input a description of your task and some test cases, and the system will generate, test, and rank a multitude of prompts to find the ones that perform the best.**

## New Features (March 2024)

### Claude 3 Opus Version
I've added a new version of gpt-prompt-engineer that takes full advantage of Anthropic's Claude 3 Opus model. This version auto-generates test cases and allows for the user to define multiple input variables, making it even more powerful and flexible. Try it out with the claude-prompt-engineer.ipynb notebook in the repo!

### Claude 3 Opus -> Haiku Conversion Version
This notebook enables you to build lightning-fast, performant AI systems at a fraction of the typical cost. By using Claude 3 Opus to establish the latent space and Claude 3 Haiku for the actual generation, you can achieve amazing results. The process works by leveraging Opus to produce a collection of top-notch examples, which are then used to guide Haiku in generating output of comparable quality while dramatically reducing both latency and cost per generation. Try it out with the opus-to-haiku-conversion.ipynb notebook in the repo!

## Features

- **Prompt Generation**: Using GPT-4, GPT-3.5-Turbo, or Claude 3 Opus, `gpt-prompt-engineer` can generate a variety of possible prompts based on a provided use-case and test cases.

- **Prompt Testing**: The real magic happens after the generation. The system tests each prompt against all the test cases, comparing their performance and ranking them using an ELO rating system.

- **ELO Rating System**: Each prompt starts with an ELO rating of 1200. As they compete against each other in generating responses to the test cases, their ELO ratings change based on their performance. This way, you can easily see which prompts are the most effective.

- **Classification Version**: The `gpt-prompt-engineer -- Classification Version` notebook is designed to handle classification tasks. It evaluates the correctness of a test case by matching it to the expected output ('true' or 'false') and provides a table with scores for each prompt.

- **Claude 3 Version**: The claude-prompt-engineer notebook is designed to work with Anthropic's Claude 3 Opus model. It auto-generates test cases and allows for multiple input variables, making it even more powerful and flexible.

- **Claude 3 Opus -> Haiku Conversion Version**: Designed to preserve Opus' quality for your use-case while getting the speed + cost benefits of using Haiku.

- **[Weights & Biases](https://wandb.ai/site/prompts) Logging**: Optional logging to [Weights & Biases](https://wandb.ai/site) of your configs such as temperature and max tokens, the system and user prompts for each part, the test cases used and the final ranked ELO rating for each candidate prompt. Set `use_wandb` to `True` to use. 

- **[Portkey](https://portkey.ai)**: Optional tool to log and trace all the prompt chains and their responses. Set `use_portkey` to `True` to use.

## Setup

1. Open the appropriate notebook in Google Colab:
   - [Main Version](https://colab.research.google.com/github/mshumer/gpt-prompt-engineer/blob/main/gpt_prompt_engineer.ipynb)
   - [Classification Version](https://colab.research.google.com/drive/16NLMjqyuUWxcokE_NF6RwHD8grwEeoaJ?usp=sharing)
   - [Claude 3 Version](https://colab.research.google.com/drive/1likU_S4VfkzoLMPfVdMs3E54cn_W6I7o?usp=sharing)

2. Add your API key:
   - For GPT versions: `openai.api_key = "ADD YOUR KEY HERE"`
   - For Claude 3 version: `ANTHROPIC_API_KEY = "ADD YOUR KEY HERE"`

## Usage Examples

### Main Version
```python
description = "Given a prompt, generate a landing page headline."

test_cases = [
    {
        'prompt': 'Promoting an innovative new fitness app, Smartly',
    },
    {
        'prompt': 'Why a vegan diet is beneficial for your health',
    }
    # Add more test cases as needed
]
```

### Classification Version
```python
test_cases = [
    {
        'prompt': 'I had a great day!',
        'output': 'true'
    },
    {
        'prompt': 'I am feeling gloomy.',
        'output': 'false'
    }
    # Add more test cases as needed
]
```

### Claude 3 Version
```python
description = "Given a prompt, generate a personalized email response."

input_variables = [
    {"variable": "SENDER_NAME", "description": "The name of the person who sent the email."},
    {"variable": "RECIPIENT_NAME", "description": "The name of the person receiving the email."},
    {"variable": "TOPIC", "description": "The main topic or subject of the email. One to two sentences."}
]
```

## Contributing

Contributions are welcome! Some ideas for improvements:
- Create different system prompt generators for various styles (examples, verbose, short, markdown, etc.)
- Implement automatic test case generation
- Expand the classification version to support multiple classes using tiktoken

## License

This project is [MIT](https://github.com/your_username/your_repository/blob/master/LICENSE) licensed.

## Contact

- Matt Shumer - [@mattshumer_](https://twitter.com/mattshumer_)
- Project Link: [https://github.com/mshumer/gpt-prompt-engineer](https://github.com/mshumer/gpt-prompt-engineer)

---

If you're interested in something even more advanced, check out [HyperWrite Personal Assistant](https://app.hyperwriteai.com/personalassistant). It's an AI with access to real-time information that excels at natural writing and can operate your web browser to complete tasks.

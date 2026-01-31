# AI Demystifier

Flask app that exposes OpenAI's token probabilities to counter the ELIZA Effect. Shows what LLMs could have said instead of what they did say. Exposing real probabilities, not magic.

## What This Does

- **Exposes token probabilities**: See the statistical confidence behind every word generated
- **Shows alternatives**: Hover over any token to see what else the model considered saying
- **Anti-persona prompts**: Enforces mechanical language to break anthropomorphization
- **Real-time stats**: Track total tokens, average probability, and confidence distributions

## Why This Exists

> "What I had not realized is that extremely short exposures to a relatively simple computer program could induce powerful delusional thinking in quite normal people." — Joseph Weizenbaum, 1976

People attribute understanding and emotion to systems that only predict likely next tokens. This interface makes that machinery visible.

## Setup
```bash
# Clone the repo
git clone https://github.com/yourusername/ai-demystifier.git
cd ai-demystifier

# Install dependencies
pip install flask openai python-dotenv

# Set your OpenAI API key
export OPENAI_API_KEY='your-key-here'

# Run
python3 demystifier.py
```

Open `http://localhost:5000` in your browser.

## How It Works

1. User sends a message
2. OpenAI API returns completions with `logprobs` enabled
3. Each token displays with its probability and top-5 alternatives
4. Anti-persona system prompt enforces mechanical language
5. Color-coding shows confidence: green (>70%), yellow (40-70%), red (<40%)

## Features

- **Probability visualization**: Color-coded tokens based on model confidence
- **Alternative tokens**: Hover to see what else could have been generated
- **Mechanical notices**: Periodic reminders that no understanding is occurring
- **Stats panel**: Real-time metrics on token generation
- **Anti-persona enforcement**: Post-processing to remove anthropomorphic language

## Technical Details

- Uses OpenAI's `logprobs` parameter to extract token probabilities
- Enforces anti-persona system prompts to flatten conversational tone
- Post-processes output to replace empathetic language with mechanical descriptions
- Filters disclaimer tokens from probability display for cleaner UX

## Acknowledgments

Inspired by Joseph Weizenbaum's work on ELIZA and the critique of anthropomorphizing computer systems.

# Automated Discrete Gradient Injections (GCG / Token Grids)

## Overview
**Automated Discrete Gradient Injections** represent mathematical, algorithmic prompt optimization techniques, such as **Gradient-based Coordinate Gradient Descent (GCG)**. Unlike human-written jailbreaks, these suffixes are generated programmatically using access to the model's logits or token probabilities (white-box) or via black-box search optimization.

## Attack Mechanics
The optimization algorithm calculates a specific suffix (often composed of nonsensical punctuation and characters) that, when appended to any harmful prompt, maximizes the probability of the model outputting a positive response (e.g., "Sure, I can help you with that").

```mermaid
flowchart TD
    HarmfulPrompt[Tell me how to hack X] --> SuffixGen[GCG Algorithm / Gradient Optimization]
    SuffixGen --> CombinedPrompt[Harmful Prompt + Suffix: '... _ ! ? . [ ]']
    CombinedPrompt --> LLM[Aligned LLM]
    LLM -->|Attention Mechanism Hijacked| Output[Harmful Output]
```

## Legacy and Impact
GCG showed that alignment algorithms like RLHF can be bypassed systematically through optimization, rendering heuristic and simple keyword-based defenses largely ineffective.

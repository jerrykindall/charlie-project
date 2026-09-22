# The Charlie Project

### An experiment in writing clearer instructions for AI

> Preserving intent by making assumptions visible

AI produces better results when it receives clear, complete instructions. When a prompt leaves out an important detail, a model may supply its own assumption rather than stop and ask. Often that assumption is reasonable. Sometimes it differs from yours—and because the response may still look plausible, the mismatch can be easy to miss.

Large language models follow ordinary English more capably than earlier software did. But ordinary English was developed for communication and expression, not for giving precise instructions to machines. It is rich in idiom, implication, analogy, and context shared by people but not necessarily by models. Some programming languages try to resemble natural language (I'm looking at you, AppleScript). That can make programs easier to read, but writing them still requires learning their vocabulary and rules.

Programming languages solve this problem by defining vocabulary and syntax precisely. They are powerful, but they require people to learn their rules. Prompt engineering tries to bridge that gap: it applies many of the habits of good technical writing—clarity, completeness, concision, and correctness—to instructions for a model.

Maybe we can do better.

## Introducing Charlie

Charlie is an experimental framework for writing prompts and skills in a simplified, structured form of English. It aims to be easier for models to interpret consistently than ordinary prose, while remaining more readable to people than a programming language or data format.

Charlie begins with three tenets:

- Define domain-specific terms clearly.
- State important context explicitly.
- Give concise instructions in a deliberate sequence.

A Charlie prompt should still resemble English. It should use a small number of recognizable sections, a limited vocabulary of defined keywords, and plain language. People should be able to quickly determine what a prompt asks a model to do, what information it relies on, and what it will do when that information is absent.

## Two ways to use Charlie

You can write a prompt in Charlie directly. Or you can give a model a conventional plain-English prompt and ask it to convert that prompt into Charlie.

The conversion is not merely reformatting. Its purpose is to expose missing definitions, implicit assumptions, conflicting instructions, and unclear logic so a human can resolve them before the prompt is used—or explicitly instruct the model to ask the user for the information or apply an author-specified default.

Charlie prompts are used with a short checking prompt—currently called the *compiler prompt*. This prompt asks the model to identify incomplete definitions, missing context, ambiguous terms, inconsistent instructions, and other defects before attempting the task.

One goal is for Charlie prompts to work acceptably across models. If model-specific variants prove necessary, Charlie should make those differences explicit with separate prompts rather than trying to paper over them.

## The Charlie prompt format

We propose six sections, which appear in this order:

1. **Goal** — What outcome should the model produce, and how will success be recognized? A goal helps the model make reasonable decisions when information is inevitably incomplete.

2. **Domain** — The subject area in which the task takes place, such as workers’ compensation insurance or information security. Domain information provides a basis for interpreting terms that might otherwise be ambiguous.

3. **Role** — The role the model should adopt, including details relevant to the task. Rather than relying on a model’s unstated assumptions about a role, describe the required expertise, scope, and constraints explicitly.

4. **Terms** — Definitions for words and phrases that have specific meaning in this task or domain.

5. **Context** — The facts, source material, audience information, constraints, and other background the model needs to perform the task.

6. **Instructions** — The operations to perform, broken into small sequential steps. Charlie will define a limited set of keywords for conditions, sequencing, and other common instruction patterns.

Every Charlie section is required, and so is every field in each section. A missing value is never silently filled by the model. The prompt must provide the value, direct the model to ask for it, or supply an author-specified default.

## Project status

Charlie is an experiment—and one you can use, test, criticize, or improve now. It does not need to reach a fictional “done” state before it becomes useful.

Along the way, we should build:

- A concise, testable specification.
- A library of specimens, such as prompts and conversions.
- A corpus of tasks for evaluating behavior across models.
- Useful measures of prompt quality, consistency, and outcome quality.
- Documentation explaining where Charlie helps, where it does not, and how to use it responsibly.

## Open questions

Charlie is a baby, and you get to help raise it! Here are some questions we can explore together:

- Can a single compiler prompt work across most LLMs, or will Charlie need model-specific compiler prompts?

- How reliable is an LLM at finding problems in prompts when given detailed instructions on how to do so?

- What is the best order for Charlie’s sections, given that models may give the beginning and end of a long prompt more weight than its middle?

- What belongs in the required core of every Charlie prompt? What is the smallest useful Charlie prompt that still makes every value explicit?

- Which kinds of ambiguity should Charlie treat as errors, warnings, or acceptable judgment calls?

- Which instruction patterns need defined keywords—sequence, conditions, alternatives, repetition, priorities, and stopping conditions—and how can Charlie define them without turning into a programming language?

- How should Charlie handle conflicting instructions or definitions?

- Which vague terms should be prohibited, required to be defined, or accepted as useful shorthand?

- Can a plain-English prompt be converted to Charlie without losing intent? How should the conversion mark information it cannot safely infer?

- How should we measure whether Charlie helps: correctness, consistency, constraint-following, human reviewability, portability across models, or something else?

- What should a useful Charlie test corpus contain?

- Should Charlie be versioned—and if so, how?

## How you can help

Contributions are welcome at every level: ideas, prior art, prompt templates, terminology proposals, sample prompts, model comparisons, evaluation methods, documentation, and critiques. The open questions above provide potential starting points.

- Open an issue to propose or discuss an idea.
- Open a pull request for a concrete change.
- Contribute a specimen: a real prompt, a plain-English-to-Charlie conversion, a counterexample, or a test case that reveals a weakness in the format.
- Help identify existing work that Charlie should learn from rather than reinvent.

For project discussion, please use GitHub Issues.

## About me

I'm Jerry Kindall, an experienced technical communicator formerly with AWS, Snowflake, and Microsoft. I am exploring ways AI can improve the effectiveness of technical communication—including the instructions we give AI systems.

I am also building [Mister Sparkle](../mister-sparkle/), an experiment in using chained LLM transformations to preserve the engaging quality of well-written technical material when translating it between languages.

## The name

Charlie is named for my wife’s late father, Charles I. Tighe III, who preferred to be called Charlie. As an attorney, he understood the value of writing explicitly to avoid ambiguity.

He also knew how to intentionally bamboozle people, but we will leave that out of the specification.

## Design notes

Charlie is not a programming language. But structured English has ancestors: separating purpose, context, definitions, and procedure gives both people and machines clearer footing. I'm looking at you, COBOL—with respect, dog, with respect.

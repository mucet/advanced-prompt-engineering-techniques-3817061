# Prompt Engineering: How to Talk to the AIs — Comprehensive Study Summary & Implementation Guide

> **Core Philosophy:** *"Being able to translate your thoughts and interact with AI effectively is a universal technical skill."*

This document is an in-depth reference guide covering all the example prompts shared in the **"Prompt Engineering: How to Talk to the AIs"** course, the engineering principles behind those prompts, multi-step AI Agent workflows, multimodal use cases, recommended academic/practical resources, and the current AI model ecosystem.

---

## Table of Contents
1. [Core Building Blocks and Anatomy of Prompt Engineering](#1-core-building-blocks-and-anatomy-of-prompt-engineering)
2. [AI Agents: Travel Customer Support Workflow](#2-ai-agents-travel-customer-support-workflow)
3. [Multimodal AI Prompts](#3-multimodal-ai-prompts)
4. [Advanced Techniques for Better and More Reliable Results](#4-advanced-techniques-for-better-and-more-reliable-results)
5. [Recommended Resources and Tools for Continued Learning](#5-recommended-resources-and-tools-for-continued-learning)
6. [AI Model Ecosystem: Which Model to Use and When?](#6-ai-model-ecosystem-which-model-to-use-and-when)
7. [Quick Checklist (Prompt Design Template)](#7-quick-checklist-prompt-design-template)

---

## 1. Core Building Blocks and Anatomy of Prompt Engineering

An effective prompt is not a randomly written sentence; it is a structured instruction where context, constraints, examples, and output formats are deliberately combined. Below are the core prompt types examined in the course along with their engineering breakdowns:

### 1.1. Text-to-Image Generation Prompt
To achieve strong results in image generation models, rather than using abstract expressions, you must clearly define the **design style, color palette, composition layout, specific objects, and overall atmosphere**.

* **Prompt:**
  > *"Generate a clean, flat-design minimalist infographic, rendered in bold orange and slate gray on a clean white background, illustrating a complete marathon pacing and fueling strategy. A continuous horizontal path connects mile markers from a 'START' to a 'FINISH (26.2 miles)' arc. Two parallel rows of clear vector icons are arranged above and below the path: a series of stopwatches showing specific times and pace goals (for example, EASY, CONSERVE, DIG DEEP), along with multiple icons for water cups and energy gels. Include a large final clock showing a sub-four-hour goal achieved message. The overall style is athletic and highly structured."*

* **Engineering Breakdown (Why It Works):**
  * **Style & Medium:** `clean, flat-design minimalist infographic` (Establishes the visual genre).
  * **Color Palette:** `bold orange and slate gray on a clean white background` (Ensures high contrast and visual cohesion).
  * **Subject Matter:** `complete marathon pacing and fueling strategy` (Defines the core theme of the illustration).
  * **Spatial Layout & Composition:** `continuous horizontal path`, `two parallel rows above and below` (Guides the model on where to place objects across the canvas).
  * **Specific Details & Icons:** Stopwatches with pace goals (`EASY, CONSERVE, DIG DEEP`), water cups, energy gels, and a large final clock displaying a sub-four-hour goal message.
  * **Overall Atmosphere (Vibe):** `athletic and highly structured`.

---

### 1.2. System Context and Instructions Prompt
Assigning a **role (persona)** and a **tone of voice** to the model directly shapes the vocabulary, perspective, and depth of the generated response.

* **Prompt:**
  > *"You are an expert tour guide in Barcelona. You are helpful and polite, but also quirky and funny. Give me suggestions about main attractions, restaurants and off-the-beaten-path sights for a three-day visit to the city."*

* **Engineering Breakdown:**
  * **Identity / Role (Persona):** Expert tour guide in Barcelona (Focuses the model's knowledge retrieval geographically and professionally).
  * **Character & Tone:** Helpful, polite, yet `quirky and funny` (Produces an engaging, personable narrative rather than a dry encyclopedic list).
  * **Scope & Constraints:** A three-day timeframe covering three distinct categories: main attractions, restaurants, and `off-the-beaten-path` sights.

---

### 1.3. Question and Output Constraint/Format Prompt
Constraining **how** the model presents its answer is just as important as what it answers, significantly improving readability and utility.

* **Prompt:**
  > *"What are the top five things you recommend to visit in Barcelona? Write the output using a numbered list"*

* **Engineering Breakdown:**
  * **Quantitative Constraint:** `top five things` (Limits the response to the 5 most essential items, preventing unnecessary verbosity).
  * **Formatting Constraint:** `numbered list` (Forces a structured 1-to-5 sequence).

---

### 1.4. Instructions and Input Data Prompt
To receive tailored recommendations instead of generic advice, combine a clear **instruction** with rich **user context / input data**.

* **Prompt:**
  > *"Given the following information about me, recommend what to visit in a three-day stay in Barcelona. I am a foodie, enjoy art and music, and love hiking and the outdoors. I prefer to avoid crowds and long lines or overly touristy sites. I prefer authentic and local spots."*

* **Engineering Breakdown:**
  * **Positive Preferences:** Gastronomy (`foodie`), art, music, `hiking and the outdoors`, authentic and local spots.
  * **Negative Filters (Exclusions):** Crowds, long lines, and overly touristy sites.

---

### 1.5. Examples and Question Prompt (Few-Shot Preference Steering)
When abstract tastes are difficult to describe in words, providing the model with **positive and negative examples** is the fastest way to align its output with your preferences.

* **Prompt:**
  > *"Here are some examples of music I really like: Radiohead, Lana del Rey, and Bon Iver. I do not like Coldplay or Taylor Swift. What other music would you recommend?"*

* **Engineering Breakdown:**
  * The model identifies the stylistic intersection of the liked artists (melancholic, alternative/indie, atmospheric textures) while using the disliked artists (mainstream stadium rock / pop) to establish clear boundary lines.

---

### 1.6. Vague vs. Concrete Prompt Comparison

The vaguer a prompt is, the more generic and unpredictable the AI's response will be.

| Feature | Vague Prompt | Concrete Prompt |
| :--- | :--- | :--- |
| **Prompt Text** | *"Recommend some music I might like."* | *"Recommend five indie folk bands similar to Bon Iver or Fleet Foxes. Do not recommend any artists that have had a Top 40 Billboard hit. Format the output as a bulleted list with a one-sentence description of each band's sound."* |
| **Genre / Reference** | None (Completely open-ended) | Indie folk / Referenced to Bon Iver & Fleet Foxes |
| **Quantity Limit** | Ambiguous (`some`) | Explicit (`five bands`) |
| **Negative Constraint** | None | `No Top 40 Billboard hit` (Filters out mainstream commercial acts) |
| **Output Format** | Unstructured free text | Bulleted list + a one-sentence description of each band's sound |

---

## 2. AI Agents: Travel Customer Support Workflow

In an enterprise AI system (such as an airline customer support agent), relying on a single basic prompt can lead to costly mistakes or hallucinations. The course demonstrates the **4-stage evolution** of a reliable agent architecture through a practical case study:

### Scenario Data:
* **Airline Policy:** Pay $100 for flight delays over three hours (*except weather-related*). Pay $50 per day for lost bags.
* **Customer Email:** *"My flight was delayed four hours due to a severe storm, and my bag was lost for two days."*

---

### Step 1: Retrieval-Augmented Generation (RAG) — The Context and Baseline
To prevent the model from inventing rules from its pre-training data, the relevant company policy is injected directly into the prompt alongside the customer's email.

* **Prompt:**
  > *"Policy: Pay $100 for flight delays over three hours (except weather related). Pay $50 per day for lost bags.*
  > *Customer email: 'My flight was delayed four hours due to a severe storm, and my bag was lost for two days.'*
  > *Draft a reply."*
* **Analysis & Risk:** While the model has access to the policy, asking it to immediately `"Draft a reply"` can cause it to overlook the fact that a "severe storm" triggers the weather exception—potentially promising an incorrect $200 payout ($100 delay + $100 lost bag) instead of $100.

---

### Step 2: Adding Chain of Thought (CoT) — The Reasoning
Forcing the model to **think step by step and perform calculations before drafting the final response** drastically reduces logical and arithmetic errors.

* **Prompt:**
  > *"Policy: Pay $100 for flight delays over three hours (except weather-related). Pay $50 per day for lost bags.*
  > *Customer email: 'My flight was delayed four hours due to a severe storm, and my bag was lost for two days.'*
  > *Draft a reply but before drafting the email, think step by step to calculate the total compensation owed based strictly on the policy."*
* **Engineering Breakdown:**
  The model performs explicit intermediate reasoning first:
  1. *Flight delay:* 4 hours (meets the >3 hours threshold). However, the cause was a "severe storm" (weather-related exception applies). Delay compensation = **$0**.
  2. *Lost baggage:* Lost for 2 days. $50 per day × 2 days = **$100**.
  3. *Total Compensation Owed:* **$100**.
  Because this calculation is locked in prior to drafting the email, the resulting reply is factually accurate.

---

### Step 3: Self-Check (Reflection) — The Verification
In this stage, the model critiques and refines its own initial draft, verifying both rule compliance and communication tone.

* **Prompt:**
  > *"Review your drafted email. Are you absolutely sure you applied the weather exception correctly? Also, review the tone. Make it warmer and more empathetic before finalizing."*
* **Engineering Breakdown:**
  * Adds a secondary verification layer to catch any subtle policy misapplications.
  * Transforms a potentially robotic or blunt rejection ("We do not pay for weather delays") into a warm, empathetic customer service response that acknowledges the passenger's frustrating experience.

---

### Step 4: LLM-as-a-Judge — The Evaluation
Before the response is ever sent to the customer, it is evaluated and scored by an independent "Quality Assurance (QA) Model" configured with a dedicated evaluation prompt.

* **Prompt:**
  > *“You are a Customer Service QA Manager. Evaluate this drafted response against the Airline Policy. Score it from 1 to 5 on Policy Accuracy and Empathetic Tone. If it scores below a 4, flag it for human review."*
* **Engineering Breakdown:**
  * **Automated Quality Gate:** Any output scoring below the threshold (`< 4`) on accuracy or tone is automatically routed to a human agent (`human-in-the-loop`). This establishes enterprise-grade safety and quality assurance.

---

## 3. Multimodal AI Prompts

Modern AI systems can process and reason across **images, screenshots, charts, and audio files** alongside text. Below are the 4 key multimodal use cases highlighted in the course:

1. **Physical Diagnostics & Repair (Photo + Text):**
   * **Action:** Upload a photo of your broken bike.
   * **Prompt:** *"What is wrong here, and what tools do I need to fix it?"*
2. **Technical Debugging (Screenshot + Text):**
   * **Action:** Upload a screenshot of an error message.
   * **Prompt:** *"What does this error mean, and what should I try next?"*
3. **Data Analysis & Insight Extraction (Chart Image + Text):**
   * **Action:** Upload a chart from a report.
   * **Prompt:** *"What are the three most important trends in this chart?"*
4. **Meeting & Audio Analysis (Audio File + Text):**
   * **Action:** Upload a meeting recording (audio file).
   * **Prompt:** *"Who agreed to take on the marketing deliverables?"*

---

## 4. Advanced Techniques for Better and More Reliable Results

To get consistent, predictable, and software-ready outputs from AI systems, two core practices stand out:

### 4.1. Specify the Output Format
Instead of leaving the structure up to the model, explicitly dictate the exact data format you need:

* **Executive Summary Format (Bullet Points + One-Sentence Takeaway):**
  > *"Summarize this article in five bullet points. Then include a one-sentence takeaway at the end."*

* **Structured Table Format (Information Extraction):**
  > *"Identify AI models in the article. Extract their names, year, lab/company that developed them, and key novel capability/functionality. Return the answer as a table."*

* **Strict JSON Format for Software / API Integration:**
  > *"Extract the model names and years from the article. Respond only in valid JSON."*
  * *Engineering Note:* The instruction `"Respond only in valid JSON"` prevents the model from wrapping the JSON in conversational filler (such as *"Here is the JSON you requested:"*), preventing downstream `JSON.parse()` failures in production code.

### 4.2. Get the Model to Ask Clarifying Questions
You don't always have to write the perfect all-inclusive prompt on the first try. Using the **Flipped Interaction** pattern, you can instruct the model to interview you first to gather missing context.

* **Prompt:**
  > *"Give me recommendations for what to see during a weekend in Barcelona.*
  > *But first, ask me three clarifying questions to better understand my preferences. Ask one question at a time."*
* **Engineering Breakdown:**
  * The constraint `"Ask one question at a time"` is crucial: it prevents the model from overwhelming the user with a wall of questions and creates a natural, back-and-forth consultative dialogue.

---

## 5. Recommended Resources and Tools for Continued Learning

The course recommends the following foundational resources for progressing from basic prompt engineering to full-scale AI application engineering:

| Category | Resource / Tool Name | Description & Primary Use Case |
| :--- | :--- | :--- |
| **Hands-On Practice** | **Anthropic’s Prompt Engineering Interactive Tutorial** | Walks through prompting techniques step by step and lets you practice interactively with hands-on examples. |
| **Official Best Practices** | **OpenAI’s Prompt Engineering Guide** | Focuses on practical strategies: writing clear instructions, providing reference text, splitting complex tasks into smaller pieces, using tools, and testing changes systematically. |
| **Academic Deep Dive** | **“Prompt Design and Engineering: Introduction and Advanced Methods”** | The instructor's comprehensive academic paper covering chain-of-thought (CoT) reasoning, reflection, agents, and prompt engineering tools. |
| **Foundational Agent Paper** | **ReAct Paper (Reasoning and Acting)** | Introduced the core pattern where language models combine reasoning with actions, enabling them to interact with external tools and environments to solve tasks. |
| **Application Frameworks** | **LangChain & LangGraph** | **LangChain:** Provides common building blocks for LLM applications.<br>**LangGraph:** Focuses on building stateful, multi-step agent workflows. |
| **Programmatic Optimization** | **DSPy** | Treats prompts less as hand-written text strings and more as modular programmatic components that can be optimized automatically. |

---

## 6. AI Model Ecosystem: Which Model to Use and When?

Using the largest or most expensive model for every task is inefficient. To match the right model to your workflow, the AI landscape is organized into 5 distinct categories:

### 6.1. Fast Models: The Doers
Ideal for high-volume everyday tasks (summarization, classification, lightweight extraction) where low latency, high speed, and cost efficiency are top priorities.
* **Google:** Gemini Flash
* **Anthropic:** Claude Haiku
* **OpenAI:** GPT Mini

### 6.2. Small Open-Weight Models: The Local Heroes
Models that can be run locally on your own hardware or private cloud, making them ideal for strict data privacy, offline execution, or custom fine-tuning.
* **Gemma** (Google)
* **DeepSeek**
* **Llama** (Meta)
* **Mistral**
* **Qwen** (Alibaba)

### 6.3. Thinking Models: The Reasoners
Models designed to spend extra compute time reasoning internally before responding. Best suited for complex mathematics, advanced software architecture, scientific analysis, and multi-step strategic planning.
* **OpenAI:** ChatGPT o3 and ChatGPT-5
* **Google:** Gemini Pro Thinking
* **Anthropic:** Claude Opus, Mythos
* **DeepSeek:** DeepSeek R2

### 6.4. Text-to-Image Models
Specialized models for generating infographics, concept art, illustrations, and photorealistic imagery from text descriptions:
* **Midjourney**
* **FLUX**
* **OpenAI Image** *(formerly DALL-E)*
* **Google’s Nano Banana** *(also called Gemini Image)*

### 6.5. Text-to-Video Models
Models capable of generating cinematic video clips and animations from text prompts or reference images:
* **Google:** Veo
* **OpenAI:** Sora
* **Runway:** Gen-3 Alpha

---

## 7. Quick Checklist (Prompt Design Template)

When engineering your own prompts, use this 6-point checklist to ensure high quality and reliability:

1. **Role & Tone (Persona):** Who should the model act as, and what tone should it adopt? *(e.g., Empathetic support agent, quirky tour guide, strict QA manager)*
2. **Context & Input Data:** What policies, reference texts, or personal preferences must the model base its answer on? *(RAG context, user profile)*
3. **Concrete Task & Constraints:** Exactly how many items do you want? What should the model explicitly avoid? *(Negative constraints)*
4. **Reasoning Step (Chain of Thought):** Should the model think step by step or calculate values before generating the final answer? *("Think step by step")*
5. **Output Format:** How should the response be structured? *(Numbered list, Markdown table, valid JSON only, bullet points + one-sentence takeaway)*
6. **Verification & Clarification:** Should the model ask clarifying questions one at a time before answering, or review/critique its own draft before finalizing?

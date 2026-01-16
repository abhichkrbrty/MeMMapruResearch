# MemMapRu — Research Proposal (1-page)

## What is MemMapRu?
MemMapRu is a browser-based research instrument that externalizes “memory” from an AI chat session into a user-governed store. It sits alongside a live AI chat (e.g., ChatGPT) and suggests memory candidates, which the user can explicitly accept, edit, or reject.

## Problem
Modern AI assistants are stateless by default, and “memory” is either absent or opaque. Users lack transparent control over what is remembered, why it is remembered, and how it affects future responses. This reduces trust and makes longitudinal interaction difficult to study.

## Core Hypothesis
Memory can be treated as an observable, user-governed layer outside the model. The act of selecting what to remember is itself a measurable signal (preference, identity, constraints, corrections, boundaries).

## What the MVP will demonstrate (by Feb)
1. **Externalized memory**: memory items are captured outside the model session
2. **User governance**: the user explicitly chooses what is saved vs discarded
3. **Selectable memory as signal**: memory acceptance/rejection can be measured and categorized

## MVP System (Chrome Extension)
- Side panel overlay next to the chat interface
- Conversation capture from the DOM (incremental updates)
- Rule-based memory candidate extraction (v1)
- Human-in-the-loop controls: save / discard / edit
- Local persistence via `chrome.storage.local` (no backend)

## Why this is research-relevant
This enables controlled experiments and observational studies on:
- What users choose to store as “memory”
- How often users reject AI-suggested memory
- Whether explicit memory control increases trust and comfort
- Which memory categories create discomfort or boundary concerns

## Near-term outcomes
A working demo and a repeatable instrumentation pipeline that can support IRB/user-study planning later, without requiring model fine-tuning or cloud infrastructure.
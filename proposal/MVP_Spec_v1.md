# MemMapRu MVP Spec (v1)

## Objective
Build a research-first Chrome extension that shows a “Memory” side panel next to an AI chat and enables user-controlled memory selection + persistence.

## In-scope (v1)
- Chrome extension scaffold (Manifest V3)
- Content script injection into chat page
- Right-side overlay panel with toggle open/close
- Conversation capture from visible DOM
- Memory candidate extraction (rule-based heuristics)
- UI cards for candidates with explanation (“why suggested”)
- User actions: Save / Discard / Edit
- Persistence via `chrome.storage.local`
- Saved memory review list (view + delete)

## Out-of-scope (v1)
- No backend/cloud sync
- No embeddings/vector DB
- No user accounts
- No LLM fine-tuning
- No automatic reinjection into prompts (optional v1.5)

## Definition of “Memory” (v1)
A memory item is a user-relevant stable signal such as:
- Preferences (“I prefer concise answers”)
- Constraints (“Don’t mention X / Don’t do Y”)
- Identity/context (“I’m a research assistant at Syracuse”)
- Corrections (“No, that’s wrong — do it this way”)
- Long-term goals (“I’m building MemMapRu by Feb”)

## Memory Candidate Rules (v1)
Suggest candidates when a message contains patterns like:
- “I prefer…”, “I like…”, “I always…”
- “Don’t…”, “Never…”, “Please avoid…”
- “Remember…”, “From now on…”
- Corrections: “No, that’s wrong…”, “Actually…”
- Repeated statements across turns

## Data model (stored locally)
Each memory item:
- id
- text
- category (preference/constraint/identity/goal/correction/other)
- source (page/session)
- created_at
- status (saved/discarded)

## MVP Success Criteria
- Panel opens next to chat reliably
- Captures conversation turns
- Shows candidate memory items
- User can save/discard/edit
- Saved memory persists across refresh/reopen
- Demo can be shown live in < 3 minutes
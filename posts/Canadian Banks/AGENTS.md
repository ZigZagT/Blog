# Blog Post Workflow

How to turn a Claude.ai conversation into published blog posts.

## Inputs

- A Claude.ai conversation export (`convo.json`) placed in `posts/<topic>/`
- User direction on scope, angle, tone, and how to split into posts

## Steps

### 1. Extract raw conversation
- Parse `convo.json` (Claude.ai export format: `chat_messages[]` → `sender` + `content[]` where `type == "text"`)
- Use `jq` to extract human/assistant text exchanges, skip thinking/tool_use/tool_result blocks
- Save to `raw_conversation.txt` — this is the raw data archive

### 2. Read and understand the conversation arc
- Identify major topic shifts and thematic clusters
- Note data points, numbers, tables, and sourced claims — these carry into the posts
- Flag where the human pushed back or redirected — those moments often reveal the strongest analytical points

### 3. Decide post structure with user
- Propose how to split the conversation into separate posts
- Get user input on: scope per post, tone, audience, angle/thesis
- One conversation can yield multiple posts if the topic arc is wide enough

### 4. Write posts
- Restructure conversation-turn progression into coherent narrative arcs
- Each post stands alone — reader shouldn't need the other post or the original conversation
- Preserve the analytical tone and data from the conversation; don't water it down
- Keep the personality — if the conversation was direct and willing to challenge, the post should be too

### 5. Publish to Medium
- Render markdown to HTML (any local md→html tool works)
- Copy-paste into Medium editor
- Medium's editor preserves headings, bold, tables, and block quotes from pasted HTML

## Outputs

All artifacts stay in `posts/<topic>/`:

| File | Purpose |
|---|---|
| `convo.json` | Original conversation export (raw source) |
| `raw_conversation.txt` | Extracted text transcript (readable raw data) |
| `AGENTS.md` | This workflow file |
| `post*.md` | Final blog post(s) |

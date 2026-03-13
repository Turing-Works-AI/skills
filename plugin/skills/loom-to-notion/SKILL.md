---
name: loom-to-notion
description: Create structured "How To" documentation pages in Notion from Loom video transcripts. Use when the user wants to transform a Loom video into step-by-step documentation, convert video tutorials into written guides, or create client documentation from recorded walkthroughs.
---

# Loom to Notion Documentation

Transform Loom video transcripts into clear, structured "How To" documentation pages in Notion.

## Process Overview

1. Fetch the Loom video transcript
2. Analyze and structure the content
3. Create a Notion page with organized documentation

## Step 1: Fetch Loom Transcript

When given a Loom share URL (e.g., `https://www.loom.com/share/{video-id}`):

1. Use `web_fetch` to retrieve the Loom page
2. Extract the transcript from the page content
3. If the transcript is provided directly by the user, skip to Step 2

## Step 2: Analyze and Structure Content

Transform the transcript into documentation by:

1. **Identify the main objective** - What is the overall goal or task being explained?
2. **Extract key steps** - Break down the walkthrough into sequential steps
3. **Note important details** - Capture specific fields, settings, locations, or values mentioned
4. **Identify prerequisites** - Note any setup or initial conditions required
5. **Extract warnings or tips** - Highlight important notes, common mistakes, or best practices

## Step 3: Create Notion Page

Create a well-structured Notion page with:

### Page Structure

```markdown
# [Title: Action-oriented description of the task]

## Overview
[Brief 1-2 sentence summary of what this documentation covers]

## Prerequisites
[List any required setup, accounts, permissions, or initial state]

## Steps

### 1. [First Major Step]
[Detailed instructions for this step]
- Specific actions to take
- Fields to fill or settings to configure
- Expected outcomes

### 2. [Second Major Step]
[Continue with numbered sections for each major step]

### 3. [Additional Steps as needed]
[Keep numbering sequential]

## Important Notes
- [Key warnings, tips, or common gotchas]
- [Configuration details to remember]

## Summary
[Quick recap of the process and final verification steps]
```

### Formatting Guidelines

- **Use clear, action-oriented headers** - Start with verbs (e.g., "Add New Client", "Configure Settings")
- **Number major steps** - Use numbered headings (###) for sequential steps
- **Use bullet points sparingly** - Only for lists of items, settings, or related actions
- **Bold key terms** - Highlight important field names, buttons, or UI elements
- **Include specific values** - When the video mentions exact text, IDs, or configurations, include them
- **Preserve context** - Mention which UI, dashboard, or tool each step occurs in
- **Keep it concise** - Remove filler words and conversational elements from the transcript

### Content Transformation

When converting transcript to documentation:

- **Remove timestamping references** - No need to mention "here" or "then" from the video
- **Convert verbal instructions to written steps** - "Click this" becomes "Click the [specific button name]"
- **Add structure to unstructured speech** - Group related actions together
- **Clarify pronouns** - Replace "it", "this", "that" with specific nouns
- **Expand abbreviations on first use** - Unless they're well-known in context

## When to Use This Skill

- User provides a Loom video URL and asks for documentation
- User has a Loom transcript and wants it converted to a Notion page
- User asks to "document this video" or "create a how-to guide"
- User mentions "client documentation" or "process documentation" from a recording

## Notes

- If the Loom video requires authentication to access, inform the user that they need to provide the transcript directly
- The transcript may contain verbal filler ("um", "uh") which should be removed in the final documentation
- Video timestamps from transcripts don't need to be preserved in the documentation
- Focus on clarity and actionability over preserving the exact flow of the video

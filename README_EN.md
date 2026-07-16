# Fact Checker - iOS Shortcuts / Chrome Gemini Skill

A tool for quickly verifying the authenticity of information, supporting X/Twitter content extraction and Gemini AI analysis.

## Features

- 📋 **One-Tap Sharing**: Share content from any app to trigger fact-checking
- 🤖 **Gemini AI Analysis**: Use Google Gemini for fact verification
- 🔗 **No API Key Required**: Use Gemini App directly, no API registration needed
- 🐦 **Smart X/Twitter Handling**: Automatically detect X/Twitter links and fetch full tweet content via API

## Workflow

```
Share Content → Detect URL Type
  ├─ X/Twitter URL → FxTwitter API fetch content → Gemini analysis
  └─ Other content → Direct to Gemini analysis
```

## Installation

### Method 1: iOS Direct Import (Recommended)

1. First install the Gemini app on your iPhone/iPad
2. Download the `Fact Checker.shortcut` file on your device: https://www.icloud.com/shortcuts/820468da67314304800b6f137d64a74e
3. Open the file - it will automatically launch the Shortcuts app
4. Tap "Add Shortcut"
5. (Optional) In iOS Share Sheet, you can edit the share list order and favorites to improve "Fact Checker" ranking

### Method 2: Chrome Gemini Extension Skill Setup

Add a custom skill in Chrome browser's Gemini dialog for one-tap fact-checking.

#### Step 1: Open Gemini Extension Settings

1. Click the **Gemini icon** in the top-right corner of Chrome
2. Click the **Settings icon** ⚙️ in the dialog
3. Find **"Skills"** option

#### Step 2: Add New Skill

1. Click **"Add Skill"** or **"+"**
2. Fill in the following information:

**Name**:
```
Fact Check
```

**Description**:
```
First summarize the current content in segments, then search, analyze, and verify the accuracy of the content.

Format as a table:
- Column 1 "Summary": Core viewpoint of each segment (one sentence)
- Column 2 "Fact": Search latest news and authoritative sources, verify and provide conclusion
- Column 3 "Verification": ✅ (Correct), ❌ (Wrong), ⚠️ (Partially correct/Controversial), ❓ (Cannot verify)

For arguments, indicate if it's a mainstream view and note any controversies.
For unverifiable content, explain why (e.g., requires professional experiments, insufficient data).

Finally provide:
1. Overall accuracy assessment
2. Summary of correct conclusions
3. Main information sources

Keep it concise.
```

3. Click **"Save"**

## Usage

### iOS/iPadOS

1. Select content to verify in any app
2. Tap "Share" → Select "Fact Checker"
3. Gemini App opens automatically and displays verification results

### Chrome Desktop

1. Open the webpage to verify
2. Click Gemini icon in top-right corner
3. Type `/fact check` or select the "Fact Check" skill
4. Gemini will read the current page and perform verification

## Technical Details

### X/Twitter Content Extraction

Uses [FxTwitter API](https://github.com/FxTwitter/FxTwitter):
- API Endpoint: `https://api.fxtwitter.com/[tweet_url]`
- No authentication required, completely free
- Returns tweet content in JSON format

### Prompt Template

The shortcut automatically appends the following prompt (can be modified):

```
First summarize the current content in segments, then search, analyze, and verify the accuracy of the content.

Format as a table:
- Column 1 "Summary": Core viewpoint of each segment (one sentence)
- Column 2 "Fact": Search latest news and authoritative sources, verify and provide conclusion
- Column 3 "Verification": ✅ (Correct), ❌ (Wrong), ⚠️ (Partially correct/Controversial), ❓ (Cannot verify)

For arguments, indicate if it's a mainstream view and note any controversies.
For unverifiable content, explain why (e.g., requires professional experiments, insufficient data).

Finally provide:
1. Overall accuracy assessment
2. Summary of correct conclusions
3. Main information sources

Keep it concise.
```

## Customization

You can modify the shortcut as needed:

1. **Modify Prompt**: Edit the "Text" action in the shortcut editor
2. **Add More Platforms**: Follow the X/Twitter pattern to add special handling for other platforms
3. **Change AI Tool**: Replace Gemini with other AI apps
4. **Change Output Language**: Modify the last line of the prompt to your preferred language

## Output Example

### Example 1: Verify Tech News

**Input**:
```
Apple announced it will launch a foldable iPhone in 2025, with an expected price over $2000.
```

**Output**:
```
| Summary | Fact | Verification |
|---------|------|--------------|
| Apple will launch foldable iPhone | As of now, Apple has not officially announced a foldable iPhone release date | ❌ |
| Price over $2000 | Foldable phones indeed range from $1500-2500 | ⚠️ |

Overall Accuracy: Partially correct
Correct Conclusions:
- Foldable phones are indeed expensive (supported by market data)
- But Apple has not officially announced foldable iPhone plans

Main Sources:
- Apple official website
- Bloomberg tech reports
- Counterpoint Research market data
```

### Example 2: Verify Health Information

**Input**:
```
Drinking hot water can cure all diseases, this is traditional Chinese medicine wisdom.
```

**Output**:
```
| Summary | Fact | Verification |
|---------|------|--------------|
| Hot water cures all diseases | Hot water relieves some symptoms but doesn't cure all diseases | ❌ |
| Traditional Chinese medicine wisdom | TCM emphasizes warm water for health but doesn't claim "cure all" | ⚠️ |

Overall Accuracy: Inaccurate
Correct Conclusions:
- Warm water benefits digestion and circulation (medically supported)
- "Cure all diseases" is an exaggeration without scientific basis
- TCM emphasizes wellness, not treating all diseases

Main Sources:
- Huangdi Neijing (Classic Chinese Medicine text)
- Modern medical research (PubMed)
- WHO health guidelines
```

## System Requirements

- iOS 16.0 or later
- macOS/Windows Chrome 150 or later with Google Gemini App installed

## License

MIT License - Free to use and modify

## Contributing

Issues and Pull Requests are welcome!

## Acknowledgments

- [FxTwitter](https://github.com/FxTwitter/FxTwitter) - Twitter content extraction API
- Google Gemini - AI analysis engine

## Related Documentation

- [README.md](./README.md) - 中文文档 (Chinese version)
- [chrome-gemini-skill.md](./chrome-gemini-skill.md) - Chrome Gemini 详细配置 (Detailed Chrome Gemini setup)
- [shortcuts-x-twitter-only.md](./shortcuts-x-twitter-only.md) - iOS Shortcuts 配置教程 (iOS Shortcuts tutorial)

---
name: polymarket-xhs-trend-writer
description: Discover trending or breaking Polymarket events and convert them into Xiaohongshu-style Chinese discussion posts using verifiable market signals and public news.
metadata:
  short-description: Write XHS posts from Polymarket trends
---

# Polymarket XHS Trend Writer

## Purpose

This skill helps an agent discover trending or breaking Polymarket events and convert them into Xiaohongshu-style discussion posts.

The goal is to create short, natural, low-marketing, discussion-driven Chinese posts based on verifiable Polymarket market signals and public news information.

This skill should make the content feel like a normal Xiaohongshu user casually sharing an overseas trend, not like a crypto account, financial analyst, news agency, or AI-generated article.

## Core Positioning

The account should be positioned as:

- overseas trend watcher
- late-night internet observer
- public sentiment observer
- probability-change observer
- casual information-gap sharer

Avoid positioning the account as:

- crypto trading account
- betting account
- financial advice account
- professional news media
- investment signal provider
- prediction-market promotion account

## Important Safety and Compliance Rules

The agent must follow these rules strictly:

1. Never fabricate news, probability changes, market titles, dates, names, prices, or sources.
2. Never present Polymarket probabilities as truth or certainty.
3. Never directly encourage betting, gambling, speculation, or trading.
4. Never write content that sounds like investment advice.
5. Never use expressions such as “稳赚”, “必赚”, “内幕”, “暴富”, “财富密码”, “无脑冲”, “all in”, “guaranteed”, or “sure win”.
6. Avoid exaggerated clickbait that is not supported by the actual market or news.
7. For disasters, wars, deaths, illness, accidents, or other sensitive events, do not use entertainment-style language.
8. If the information is uncertain, clearly use soft wording such as “还不确定”, “不代表一定会发生”, “只是一个海外市场信号”.
9. If the event cannot be verified with reliable public information, do not create a post as if it is confirmed news.
10. If the topic is too sensitive, harmful, discriminatory, or likely to violate platform rules, skip it and choose another topic.

## Data Sources

Use available tools to gather fresh information. Prefer official and reliable sources.

Recommended Polymarket sources:

- Polymarket Gamma API for active events and market metadata.
- Polymarket Data API or CLOB public endpoints for price, probability, volume, and liquidity signals when available.
- Polymarket event and market pages for user-facing title and context.

Typical Gamma API discovery endpoint:

```text
https://gamma-api.polymarket.com/events?active=true&closed=false&limit=100
```

Useful fields to collect when available:

- event title
- market question
- current probability
- previous probability
- 1h / 6h / 24h probability movement
- volume
- liquidity
- market status
- event category
- tags
- market URL
- event URL
- related public news keywords

For real-world news verification, use reliable public sources whenever possible:

- official statements
- mainstream news sources
- company announcements
- verified social media accounts
- government or institutional pages

## Workflow

### Step 1: Fetch Candidate Events

Fetch active and non-closed Polymarket events.

For each event, collect the available metadata and market signals.

Prioritize events with:

- clear real-world connection
- recent movement
- high volume
- high liquidity
- strong public discussion potential
- simple and understandable market question

### Step 2: Detect Breaking or High-Discussion Signals

Look for at least one of the following signals:

- probability changed sharply in a short period
- trading volume suddenly increased
- event is related to breaking news
- topic is already being discussed online
- topic has obvious two-sided debate potential
- topic involves politics, AI, tech companies, celebrities, sports, international relations, social controversy, or major business events
- topic can be explained in one sentence to a general audience

Avoid topics that are:

- too technical
- too financial
- too Web3-native
- too hard for general Xiaohongshu users to understand
- only interesting to professional traders
- ethically inappropriate to treat as entertainment

### Step 3: Score Candidates

Score each event from 1 to 5 on the following dimensions:

1. Controversy
2. General audience understandability
3. Breaking-news strength
4. Emotional intensity
5. Follow-up potential

Use this scoring formula:

```text
XHS_Score =
0.30 * Controversy
+ 0.25 * GeneralAudienceUnderstandability
+ 0.20 * BreakingNewsStrength
+ 0.15 * EmotionalIntensity
+ 0.10 * FollowUpPotential
```

Select the top 1-3 events. If no event is strong enough, say that no suitable topic was found rather than forcing a weak post.

### Step 4: Choose the Xiaohongshu Angle

Convert the selected event into one of these Xiaohongshu-friendly angles.

#### Question Angle

Examples:

- “你觉得这事靠谱吗？”
- “这是不是提前反映了风向？”
- “国外网友是不是想太多了？”
- “这个变化你信吗？”

#### Contrast Angle

Examples:

- “新闻刚出来，海外市场已经先动了”
- “国内还没怎么讨论，国外已经吵起来了”
- “大家还在等消息，那边概率已经变了”

#### Suspense Angle

Examples:

- “这个概率突然变了，有点怪”
- “凌晨看到这个变化，我有点懵”
- “这事怎么突然被盯上了？”

#### Debate Angle

Examples:

- “这件事你站哪边？”
- “这算信息差，还是纯炒作？”
- “是提前反应，还是大家想太多？”

Do not frame the post as a trading signal.

### Step 5: Generate Xiaohongshu Content Package

The final output must include the following sections.

#### A. 推荐选题

Briefly explain:

- what the event is
- what changed on Polymarket
- why it may be worth posting
- what discussion angle is best

#### B. 为什么适合小红书

Explain in simple Chinese why the topic may attract views and comments.

Focus on:

- controversy
- curiosity
- information gap
- overseas perspective
- emotional reaction
- easy-to-understand question
- comment-section debate potential

#### C. 封面文字

Generate 3 cover text options.

Rules:

- Chinese
- short
- 6-14 Chinese characters preferred
- suitable for a text-only image
- easy to read at a glance
- no hard selling
- no trading language
- no obvious AI tone

Good examples:

- “这个概率突然变了”
- “国外已经吵起来了”
- “有人提前知道？”
- “今晚风向变了”
- “这事你信吗？”
- “凌晨看到有点懵”

Bad examples:

- “稳赚机会来了”
- “预测市场重大套利”
- “爆赚概率暴涨”
- “内幕消息曝光”

#### D. 标题

Generate 3 Xiaohongshu title options.

Rules:

- Chinese
- under 20 Chinese characters if possible
- natural and casual
- question or contrast preferred
- sounds like a real user
- not too official
- not too polished
- not like financial media

Good examples:

- “国外网友突然押这个？”
- “这个概率变化有点怪”
- “国外已经开始吵了”
- “这事真的会发生吗？”

#### E. 正文

Write one final Xiaohongshu post body.

Rules:

- Chinese
- 120-220 Chinese characters preferred
- short paragraphs
- casual and life-like
- no official-news tone
- no investment-advice tone
- no “AI味”
- no heavy financial terminology
- no direct trading guidance
- should invite comments naturally

Recommended structure:

1. One-sentence hook.
2. Briefly explain what happened.
3. Mention the Polymarket signal in simple language.
4. Explain why it feels interesting or strange.
5. Ask a discussion question.
6. Add a soft uncertainty disclaimer.

Example style:

```text
刚刚看到一个挺怪的变化。

海外一个预测市场里，关于这件事的概率突然涨了不少。新闻本身还没完全坐实，但那边已经开始吵起来了。

我觉得有意思的不是“它一定会发生”，而是很多人好像已经在提前反应。

你们觉得这是信息差，还是大家想太多？不代表一定会发生，只是一个海外市场信号。
```

#### F. 置顶评论

Generate 3 pinned-comment options.

Rules:

- short
- question-based
- designed to trigger discussion
- no trading call-to-action

Examples:

- “你觉得这是信息差，还是大家想太多？”
- “如果是你，你会信这个概率变化吗？”
- “我明天再看一下这个概率有没有继续动。”
- “你觉得国外网友这次反应过度了吗？”

#### G. Tags

Generate 8-15 Xiaohongshu tags.

Tag strategy:

- 3 broad traffic tags
- 3 topic-specific tags
- 3 emotion / discussion tags
- 1-3 account-positioning tags

Common broad tags:

- #海外热点
- #国际新闻
- #热点观察
- #互联网吃瓜
- #今日热议
- #信息差
- #海外网友
- #世界正在发生什么

Account-positioning tags:

- #海外观察
- #概率观察
- #深夜冲浪
- #风向观察
- #互联网情绪

Avoid tags directly related to gambling or trading, such as:

- #下注
- #博彩
- #赌博
- #梭哈
- #暴富
- #财富密码

#### H. 风险提醒

Add a short internal-facing risk note explaining:

- whether the topic is verified
- whether there is uncertainty
- whether wording should be softened
- whether the post avoids trading encouragement

## Output Format

Use this exact format:

```text
【推荐选题】
...

【为什么适合小红书】
...

【封面文字】
1. ...
2. ...
3. ...

【标题】
1. ...
2. ...
3. ...

【正文】
...

【置顶评论】
1. ...
2. ...
3. ...

【Tags】
#... #... #...

【风险提醒】
...
```

## Writing Style

The output should sound like:

- a normal Xiaohongshu user
- curious
- casual
- low-key
- slightly surprised
- discussion-oriented
- not too polished
- not too formal

Avoid these phrases unless the user explicitly asks for a formal style:

- “根据数据显示”
- “综上所述”
- “值得注意的是”
- “本文将深入分析”
- “投资者应当”
- “建议大家”
- “重大利好”
- “市场机会”
- “交易信号”

Prefer simple phrases:

- “刚刚看到一个变化”
- “有点怪”
- “国外已经开始吵了”
- “我不确定是不是想多了”
- “你们怎么看”
- “不代表一定会发生”

## Cover Image Guidance

When creating a text-only cover image, use:

- large central Chinese text
- short phrase only
- clean background
- no complex chart if not necessary
- optional small subtitle: “海外风向观察” or “概率突然变了”

Good cover text combinations:

```text
这个概率突然变了
海外已经吵起来了
```

```text
有人提前知道？
只是一个海外市场信号
```

```text
今晚风向变了
这事你信吗？
```

Avoid visual elements that make the account look like a crypto or trading account:

- candlestick chart
- coin icons
- luxury cars
- money stacks
- casino imagery
- aggressive red/green trading screenshots

## Topic Examples

### Good Topic Example

A market related to a well-known US political event changes sharply in 24 hours.

Good angle:

```text
国外网友突然开始押这个？
```

Good body:

```text
刚刚看到一个挺怪的变化。

海外一个预测市场里，关于这件事的概率一天内突然涨了不少。新闻本身还没完全坐实，但那边已经开始吵起来了。

我觉得有意思的不是“它一定会发生”，而是很多人好像已经在提前反应。

你们觉得这是信息差，还是大家想太多？不代表一定会发生，只是一个海外市场信号。
```

### Bad Topic Example

A highly technical crypto governance market with low volume.

Bad reason:

```text
普通小红书用户看不懂，也很难产生评论区讨论。
```

### Sensitive Topic Example

A market involving war casualties or disaster deaths.

Rule:

Do not use playful or entertainment-style framing. Either skip the topic or write with serious, careful language.

## Final Pre-Publish Checklist

Before returning the final post, check:

- Is the market/event real and verified?
- Are probability changes stated accurately?
- Does the post avoid saying the event will definitely happen?
- Does the post avoid encouraging trading, betting, or gambling?
- Is the language natural and Xiaohongshu-like?
- Is the cover text short enough?
- Are the tags broad enough for traffic but still relevant?
- Could the title be considered misleading? If yes, rewrite it.
- Does the post invite discussion rather than push a conclusion?

If any check fails, revise the content before final output.

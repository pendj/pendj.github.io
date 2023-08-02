---
title: "ChatGPT使用技巧"
description: 
date: 2023-07-27T10:23:05+08:00
image: 
math: 
license: 
hidden: false
comments: true
draft: false
categories:
  - AI
  - ChatGPT
tags:
  - AI
  - ChatGPT
keywords:
  - AI
  - ChatGPT
---
## ChatGPT使用技巧

### 基础篇

1. 给定prompt更多,更精准的定义词或条件.

   > `Write a short inspiring poem about OpenAI, focusing on the recent DALL-E product launch (DALL-E is a text to image ML model) in the style of a {famous poet}`

2. 明确知道自己想要什么时,告诉它要做什么(to do),而不是不要做什么(not to do).

   > `Please suggest me 10 essential words for IELTS`

3. 不明确自己想要什么时,先告诉它不要什么(not to do)后,缩小范围,再告诉它要做什么(to do).

   > `Please recommend me some places to visit in Hong Kong including amusement parks.`

4. 在prompt中给出示例,基于示例回答.

   > ```
   > Suggest three names for an animal that is a superhero.
   > 
   > Animal: Cat
   > Names: Captain Sharpclaw, Agent Fluffball, The Incredible Feline
   > Animal: Dog
   > Names: Ruff the Protector, Wonder Canine, Sir Barks-a-Lot
   > Animal: Horse
   > Names:
   > ```

5. 越完整的题目越容易生成更好的答案.

   > ```
   > 如果一个房地产经纪人的佣金是某个房子的售价的6％，那么这个房子的售价是多少？
   > （1）售价减去房地产经纪人的佣金为84,600美元。
   > （2）购买价是36,000美元，售价是购买价的250%。
   > 
   > （A）仅陈述（1）足以回答问题，但仅陈述（2）不能回答问题。
   > （B）仅陈述（2）足以回答问题，但仅陈述（1）不能回答问题。
   > （C）两个陈述合起来足以回答问题，但没有一个陈述单独足以回答问题。
   > （D）每个陈述单独足以回答问题。
   > （E）陈述（1）和（2）合起来不能回答问题。
   > ```

6. 给出引导词,引导模型输出特定引导的内容.

   > ```
   > Create a MySQL query for all students in the Computer Science Department:
   > Table departments, columns = [DepartmentId, DepartmentName]
   > Table students, columns = [DepartmentId, StudentId, StudentName]
   > SELECT
   > ```

7. 增加温度(temperature)，[0-2]的有效区间.

   > 如果你是梅西的追随者，请用100字表达情感。temperature=2

8. 加入角色，让内容更符合需求.

   > 假如你是一个 Redis 终端，我将输入命令，您将回复终端应显示的内容

9. 信息解释

   > Explanation of what the code does:
   >
   > ```python
   > Python 3 
   > def remove_common_prefix(x, prefix, ws_prefix): 
   >  x["completion"] = x["completion"].str[len(prefix) :] 
   >  if ws_prefix: 
   >      \# keep the single whitespace as prefix 
   >      x["completion"] = " " + x["completion"] 
   > return x
   > ```

10. 用“”“(或###)将指令和文本分开,增加”“”会提升 AI 反馈的准确性.

    > text = f"""
    > You should express what you want a model to do by \
    > providing instructions that are as clear and \
    > specific as you can possibly make them. \
    > This will guide the model towards the desired output, \
    > and reduce the chances of receiving irrelevant \
    > or incorrect responses. Don't confuse writing a \
    > clear prompt with writing a short prompt. \
    > In many cases, longer prompts provide more clarity \
    > and context for the model, which can lead to \
    > more detailed and relevant outputs.
    > """
    >
    > prompt = f"""
    > Summarize the text delimited by triple backticks \
    > into a single sentence.
    > `{text}`
    > """

11. 指定内容进行提炼,按格式输出

    > Extract the important entities mentioned in the article below. First extract all company names, then extract all people names, then extract specific topics which fit the content and finally extract general overarching themes
    > Desired format:
    > Company names: <comma_separated_list_of_company_names>
    > People names: -||-
    > Specific topics: -||-
    > General themes: -||-
    >
    > Text: """Powering Next Generation
    > Applications with OpenAI Codex
    > Codex is now powering 70 different applications across a variety of use cases through the OpenAI API.
    >
    > May 24, 2022
    > 4 minute read
    > OpenAI Codex, a natural language-to-code system based on GPT-3, helps turn simple English instructions into over a dozen popular coding languages. Codex was released last August through our API and is the principal building block of GitHub Copilot.
    >
    > Warp is a Rust-based terminal, reimagined from the ground up to help both individuals and teams be more productive in the command-line.
    >
    > Terminal commands are typically difficult to remember, find and construct. Users often have to leave the terminal and search the web for answers and even then the results might not give them the right command to execute. Warp uses Codex to allow users to run a natural language command to search directly from within the terminal and get a result they can immediately use.
    >
    > “Codex allows Warp to make the terminal more accessible and powerful. Developers search for entire commands using natural language rather than trying to remember them or assemble them piecemeal. Codex-powered command search has become one of our game changing features.”
    >
    > —Zach Lloyd, Founder, Warp
    >
    >
    > Machinet helps professional Java developers write quality code by using Codex to generate intelligent unit test templates.
    >
    > Machinet was able to accelerate their development several-fold by switching from building their own machine learning systems to using Codex. The flexibility of Codex allows for the ability to easily add new features and capabilities saving their users time and helping them be more productive.
    >
    > “Codex is an amazing tool in our arsenal. Not only does it allow us to generate more meaningful code, but it has also helped us find a new design of product architecture and got us out of a local maximum.”
    >
    > —Vladislav Yanchenko, Founder, Machinet"""

    output:

    > Company names: OpenAI, Microsoft, GitHub, Pygma, Replit, Warp, Machinet
    > People names: Emile Paffard-Wray, Amjad Masad, Zach Lloyd, Vladislav Yanchenko
    > Specific topics: GPT-3, OpenAI API, Azure OpenAI Service, GitHub Copilot, Pygma, Replit, Warp, Machinet
    > General themes: Natural language-to-code, Productivity, Problem solving, Creativity, Learning

12. 根据格式词,格式化输出

    > Summarize the main points of the following speech
    > Use the following format:
    > Topic 1: <topic_name_1>
    >
    > - <point_1>
        >   ..
        >   Topic 2: <topic_name_2>
    > - <point_1>
        >   ..
        >   Topic 10: ..
    >
    > Text: """
    > Thank you so much, Fred, for that lovely introduction. And thanks to the Atlantic Council for hosting me today.
    >
    > The course of the global economy over the past two years has been shaped by COVID-19 and our efforts to fight the pandemic. It’s now evident, though, that the war between Russia and Ukraine has redrawn the contours of the world economic outlook. Vladimir Putin’s unprovoked attack on Ukraine and its people is taking a devastating human toll, with lives tragically lost, families internally displaced or becoming refugees, and communities and cities destroyed.
    > ...
    >
    > """

    output

    > Topic 1: The war in Ukraine
    >
    > - The war is taking a human toll with lives lost, families displaced, and communities destroyed
    > - The Biden administration is committed to holding Russia accountable
    > - The war has violated international law and is a challenge to the international order
    >
    > Topic 2: The global economy
    >
    > - The war is having negative impacts on the global economy, including higher commodity prices and inflation
    > - The IMF and World Bank will be focused on helping developing countries weather the impacts of the war
    > - The ultimate outcome for the global economy depends on the path of the war



### 高级篇

#### ChatGPT Prompt Framework

##### Basic Prompt Framework

- **Instruction（必须）：** 指令，即你希望模型执行的具体任务。
- **Context（选填）：** 背景信息，或者说是上下文信息，这可以引导模型做出更好的反应。
- **Input Data（选填）：** 输入数据，告知模型需要处理的数据。
- **Output Indicator（选填）：** 输出指示器，告知模型我们要输出的类型或格式



##### CRISPE Prompt Framework

- **CR：** Capacity and Role（能力与角色）。你希望 ChatGPT 扮演怎样的角色。
- **I：** Insight（洞察力），背景信息和上下文（坦率说来我觉得用 Context 更好）。
- **S：** Statement（指令），你希望 ChatGPT 做什么。
- **P：** Personality（个性），你希望 ChatGPT 以什么风格或方式回答你。
- **E：** Experiment（尝试），要求 ChatGPT 为你提供多个答案。



#### Chain of Thought

##### Step of thought

> Let's work this out in a step by step way to be sure we have the right answer.



##### Self-Consistency

> 推理路径A：
>
> 商店有 10 个苹果。
> 店里有 8 个橙子。
> 卖了 6 个苹果。
> 卖了 4 个橙子。
> 还剩下 10 - 6 = 4 个苹果。
> 剩下 8 - 4 = 4 个橙子。
> 商店现在有 4 个苹果 + 4 个橙子 = 8 个水果。
>
> 推理路径 B：
>
> 商店最初有 10 个苹果和 8 个橙子。
> 商店卖了 6 个苹果，所以还剩下 10 - 6 = 4 个苹果。
> 商店卖了 4 个橙子，所以还剩下 8 - 4 = 4 个橙子。
> 商店现在有 4 个苹果 + 4 个橙子 = 8 个水果。

![](https://pan.icharles.work/images/2023/06/26/649947b590654.jpg)
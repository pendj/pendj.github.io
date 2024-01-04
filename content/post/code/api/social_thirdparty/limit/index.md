---
title: "海外分发平台API使用限额"
description: 
date: 2024-01-04T13:43:30+08:00
image: 
math: 
license: 
hidden: false
comments: true
draft: true
categories:
  - API
  - 社交媒体
  - Twitter
  - Youtube
  - Facebook
tags:
  - API
  - 社交媒体
  - Twitter
  - Youtube
  - Facebook
keywords:
  - API
  - 社交媒体
  - Twitter
  - Youtube
  - Facebook
---
### 海外分发平台API使用限额

#### Facebook/Instagram

> Facebook的访问口令:[访问口令指南 - Facebook 登录](https://developers.facebook.com/docs/facebook-login/guides/access-tokens#apptokens)
>
> 每种口令使用配额情况: [流量限制 - 图谱 API (facebook.com)](https://developers.facebook.com/docs/graph-api/overview/rate-limiting/)

| 计算方式/每小时    | 用户访问口令 | 应用程序访问口令                   | 公共主页访问口令                                             | 系统访问口令                                                 | 客户端访问口令 |
| ------------------ | ------------ | ---------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | -------------- |
| 通用               | 未透露       | 200 * 基于应用的日活跃独立用户数量 |                                                              |                                                              |                |
| 广告成效分析       |              |                                    |                                                              | 60 + 400 *每个广告帐户当前投放的广告的数量 - 0.001 * 调用 API 后收到的错误的数量 |                |
| 广告管理           |              |                                    |                                                              | 300 + 40 * 每个广告帐户的广告数量                            |                |
| 目录批处理         |              |                                    |                                                              | 200 + 200 * log2(过去 28 天内商家的有意向独立用户数)         |                |
| 目录管理           |              |                                    |                                                              | 20,000 + 20,000 * log2(过去 28 天内商家的有意向独立用户数量) |                |
| Instagram 图谱 API |              |                                    | 4800 * 过去 24 小时内来自应用用户 Instagram 帐户中的任何内容在某个用户的屏幕上显示的次数 |                                                              |                |
| 公共主页           |              |                                    | 4800 * 每 24 小时内与公共主页进行互动的用户的数量            |                                                              |                |



#### Youtube

##### 总配额

> [YouTube Data API - 配额和合规性审核  | Google for Developers](https://developers.google.com/youtube/v3/guides/quota_and_compliance_audits?hl=zh-cn)

YouTube Data API 的项目的默认配额为每天 10,000 个单元,除了默认分配以外，如果还希望申请额外的配额，则必须先完成审核.

##### API 使用额度

> [YouTube Data API (v3) - 配额计算器  | Google for Developers](https://developers.google.com/youtube/v3/determine_quota_cost?hl=zh-cn)

| 配额费用                |                     |                     |
| :---------------------- | ------------------- | ------------------- |
| 资源                    | 请求API             | 每次使用API消耗额度 |
| 活动                    | list                | 1                   |
| captions                | list                | 50                  |
|                         | insert              | 400                 |
|                         | update              | 450                 |
|                         | 删除                | 50                  |
| 频道横幅                | insert              | 50                  |
| 频道                    | list                | 1                   |
|                         | update              | 50                  |
| 渠道版块                | list                | 1                   |
|                         | insert              | 50                  |
|                         | update              | 50                  |
|                         | 删除                | 50                  |
| comments                | list                | 1                   |
|                         | insert              | 50                  |
|                         | update              | 50                  |
|                         | setModerationStatus | 50                  |
|                         | 删除                | 50                  |
| commentThread           | list                | 1                   |
|                         | insert              | 50                  |
|                         | update              | 50                  |
| 指南类别                | list                | 1                   |
| 国际化语言              | list                | 1                   |
| 国际化区域              | list                | 1                   |
| 成员                    | list                | 1                   |
| membershipLevels        | list                | 1                   |
| 播放列表项              | list                | 1                   |
|                         | insert              | 50                  |
|                         | update              | 50                  |
|                         | 删除                | 50                  |
| 播放列表                | list                | 1                   |
|                         | insert              | 50                  |
|                         | update              | 50                  |
|                         | 删除                | 50                  |
| search                  | list                | 100                 |
| subscriptions           | list                | 1                   |
|                         | insert              | 50                  |
|                         | 删除                | 50                  |
| 缩略图                  | set                 | 50                  |
| videoAbuseReportReasons | list                | 1                   |
| 视频类别                | list                | 1                   |
| 视频                    | list                | 1                   |
|                         | insert              | 1600                |
|                         | update              | 50                  |
|                         | 费率                | 50                  |
|                         | getRating           | 1                   |
|                         | 举报滥用行为        | 50                  |
|                         | 删除                | 50                  |
| 水印                    | set                 | 50                  |
|                         | 未设置              | 50                  |



#### Twitter

##### 不同等级的应用限制

> 各个等级应用的限制情况: [Twitter API 入门 |文档 |Twitter 开发者平台](https://developer.twitter.com/en/docs/twitter-api/getting-started/about-twitter-api#v2-access-leve)

|                             | 免费            | 基础    | 专业      | 企业      |
| --------------------------- | --------------- | ------- | --------- | --------- |
| 访问限制                    | 发推特,上传视频 | 全部    | 全部      | 定制化    |
| 发布限制/每月               | 1,500           | 3,000   | 300,000   |           |
| 读取限制/每月               | ❌               | 10,000  | 1,000,000 |           |
| 筛选器流 API                | ❌               | ❌       | ✔️         |           |
| 访问完整存档搜索            | ❌               | ❌       | ✔️         |           |
| 项目数量限制                | 1个             | 1个     | 1个       |           |
| 应用程序数量限制            | 1个             | 2个     | 3个       |           |
| 环境限制 (开发/生产/预生产) | 1个             | 2个     | 3个       |           |
| 登录推特                    | 是              | 是      | 是        |           |
| 访问广告API                 | 是              | 是      | 是        |           |
| 费用                        | 免费            | $100/月 | $5000/月  | 订阅费/月 |

##### 接口访问速率限制

> 各个等级应用的接口访问速率限制情况: [Rate limits | Docs | Twitter Developer Platform](https://developer.twitter.com/en/docs/twitter-api/rate-limits)

###### 免费

| 请求端点           | 请求数量 | 时间窗口 | 请求对象 | 读取权限? | 每个月的限制 |
| ------------------ | -------- | -------- | -------- | --------- | ------------ |
| POST_2_tweets      | 50       | 24 hours | per user | no        | 1,500        |
|                    | 50       | 24 hours | per app  | no        | 1,500        |
| DELETE_2_tweets_id | 50       | 24 hours | per user | no        | 1,500        |
|                    | 50       | 24 hours | per app  | no        | 1,500        |
| GET_2_users_me     | 25       | 24 hours | per user | no        | 750          |

###### 基础

| 请求端点                                          | 请求数量 | 时间窗口   | 请求对象 | 读取权限? | 每个月的限制 |
| ------------------------------------------------- | -------- | ---------- | -------- | --------- | ------------ |
| DELETE_2_lists_param                              | 5        | 15 minutes | per user | no        | 14,400       |
| DELETE_2_lists_param_members_param                | 5        | 15 minutes | per user | no        | 14,400       |
| DELETE_2_tweets_param                             | 5        | 15 minutes | per user | no        | 14,400       |
| DELETE_2_users_id_bookmarks_tweet_id              | 5        | 15 minutes | per user | no        | 14,400       |
| DELETE_2_users_param_blocking_param               | 5        | 15 minutes | per user | no        | 14,400       |
| DELETE_2_users_param_followed_lists_param         | 5        | 15 minutes | per user | no        | 14,400       |
| DELETE_2_users_param_following_param              | 5        | 15 minutes | per user | no        | 14,400       |
| DELETE_2_users_param_likes_param                  | 5        | 15 minutes | per user | no        | 14,400       |
|                                                   | 100      | 24 hours   | per user | no        | 3,000        |
| DELETE_2_users_param_muting_param                 | 5        | 15 minutes | per user | no        | 14,400       |
| DELETE_2_users_param_pinned_lists_param           | 5        | 15 minutes | per user | no        | 14,400       |
| DELETE_2_users_param_retweets_param               | 5        | 15 minutes | per user | no        | 14,400       |
| GET_2_compliance_jobs                             | 5        | 15 minutes | per app  | no        | 14,400       |
| GET_2_compliance_jobs_param                       | 5        | 15 minutes | per app  | no        | 14,400       |
| GET_2_dm_conversations_param_dm_events            | 3        | 15 minutes | per user | no        | 8,640        |
| GET_2_dm_conversations_with_param_dm_events       | 3        | 15 minutes | per user | no        | 8,640        |
| GET_2_dm_events                                   | 5        | 15 minutes | per user | no        | 14,400       |
| GET_2_lists_id                                    | 5        | 15 minutes | per user | no        | 14,400       |
|                                                   | 5        | 15 minutes | per app  | no        | 14,400       |
| GET_2_lists_id_members                            | 5        | 15 minutes | per user | no        | 14,400       |
|                                                   | 25       | 15 minutes | per app  | no        | 72,000       |
| GET_2_lists_id_tweets                             | 5        | 15 minutes | per user | yes       | 10,000       |
|                                                   | 25       | 15 minutes | per app  | yes       | 10,000       |
| GET_2_spaces                                      | 5        | 15 minutes | per user | no        | 14,400       |
|                                                   | 25       | 15 minutes | per app  | no        | 72,000       |
| GET_2_spaces_by_creator_ids                       | 5        | 15 minutes | per user | no        | 14,400       |
|                                                   | 25       | 15 minutes | per app  | no        | 72,000       |
| GET_2_spaces_param                                | 25       | 15 minutes | per app  | no        | 72,000       |
|                                                   | 5        | 15 minutes | per user | no        | 14,400       |
| GET_2_spaces_param_buyers                         | 5        | 15 minutes | per user | no        | 14,400       |
|                                                   | 25       | 15 minutes | per app  | no        | 72,000       |
| GET_2_spaces_param_tweets                         | 5        | 15 minutes | per user | no        | 14,400       |
|                                                   | 25       | 15 minutes | per app  | no        | 72,000       |
| GET_2_spaces_search                               | 5        | 15 minutes | per user | no        | 14,400       |
|                                                   | 25       | 15 minutes | per app  | no        | 72,000       |
| GET_2_tweets                                      | 15       | 15 minutes | per user | yes       | 10,000       |
|                                                   | 15       | 15 minutes | per app  | yes       | 10,000       |
| GET_2_tweets_counts_recent                        | 5        | 15 minutes | per app  | no        | 14,400       |
| GET_2_tweets_param                                | 15       | 15 minutes | per user | yes       | 10,000       |
|                                                   | 15       | 15 minutes | per app  | yes       | 10,000       |
| GET_2_tweets_param_liking_users                   | 5        | 15 minutes | per user | no        | 14,400       |
|                                                   | 25       | 15 minutes | per app  | no        | 72,000       |
| GET_2_tweets_param_quote_tweets                   | 5        | 15 minutes | per user | yes       | 10,000       |
|                                                   | 5        | 15 minutes | per app  | yes       | 10,000       |
| GET_2_tweets_param_retweeted_by                   | 5        | 15 minutes | per app  | yes       | 10,000       |
|                                                   | 5        | 15 minutes | per user | yes       | 10,000       |
| GET_2_tweets_search_recent                        | 60       | 15 minutes | per app  | yes       | 10,000       |
|                                                   | 60       | 15 minutes | per user | yes       |              |
| GET_2_users                                       | 500      | 24 hours   | per app  | no        | 15,000       |
|                                                   | 100      | 24 hours   | per user | no        | 3,000        |
| GET_2_users_by                                    | 100      | 24 hours   | per user | no        | 3,000        |
|                                                   | 500      | 24 hours   | per app  | no        | 15,000       |
| GET_2_users_by_username_param                     | 100      | 24 hours   | per user | no        | 3,000        |
|                                                   | 500      | 24 hours   | per app  | no        | 15,000       |
| GET_2_users_by_username_param_followers           | 100      | 24 hours   | per user | no        | 3,000        |
|                                                   | 500      | 24 hours   | per app  | no        | 15,000       |
| GET_2_users_by_username_param_mentions            | 25       | 15 minutes | per app  | no        | 72,000       |
|                                                   | 5        | 15 minutes | per user | no        | 14,400       |
| GET_2_users_by_username_param_tweets              | 25       | 15 minutes | per app  | yes       | 10,000       |
|                                                   | 5        | 15 minutes | per user | yes       | 10,000       |
| GET_2_users_id_bookmarks                          | 10       | 15 minutes | per user | no        | 28,800       |
| GET_2_users_id_list_memberships                   | 25       | 15 minutes | per app  | no        | 72,000       |
|                                                   | 5        | 15 minutes | per user | no        | 14,400       |
| GET_2_users_id_owned_lists                        | 500      | 24 hours   | per app  | no        | 15,000       |
|                                                   | 100      | 24 hours   | per user | no        | 3,000        |
| GET_2_users_id_pinned_lists                       | 100      | 24 hours   | per user | no        | 3,000        |
|                                                   | 500      | 24 hours   | per app  | no        | 15,000       |
| GET_2_users_me                                    | 250      | 24 hours   | per user | no        | 7,500        |
| GET_2_users_param                                 | 500      | 24 hours   | per user | no        | 15,000       |
|                                                   | 100      | 24 hours   | per app  | no        | 3,000        |
| GET_2_users_param_blocking                        | 5        | 15 minutes | per user | no        | 14,400       |
| GET_2_users_param_following_spaces                | 5        | 15 minutes | per user | no        | 14,400       |
|                                                   | 25       | 15 minutes | per app  | no        | 72,000       |
| GET_2_users_param_liked_tweets                    | 5        | 15 minutes | per app  | yes       | 10,000       |
|                                                   | 5        | 15 minutes | per user | yes       | 10,000       |
| GET_2_users_param_mentions                        | 15       | 15 minutes | per app  | yes       | 10,000       |
|                                                   | 10       | 15 minutes | per user | yes       | 10,000       |
| GET_2_users_param_muting                          | 100      | 24 hours   | per user | no        | 3,000        |
| GET_2_users_param_timelines_reverse_chronological | 5        | 15 minutes | per user | no        | 14,400       |
| GET_2_users_param_tweets                          | 10       | 15 minutes | per app  | yes       | 10,000       |
|                                                   | 5        | 15 minutes | per user | yes       | 10,000       |
| POST_2_compliance_jobs                            | 15       | 15 minutes | per app  | no        | 43,200       |
| POST_2_dm_conversations                           | 5        | 15 minutes | per user | no        | 14,400       |
|                                                   | 500      | 24 hours   | per app  | no        | 15,000       |
|                                                   | 50       | 24 hours   | per user | no        | 1,500        |
| POST_2_dm_conversations_param_messages            | 500      | 24 hours   | per app  | no        | 15,000       |
|                                                   | 50       | 24 hours   | per user | no        | 1,500        |
|                                                   | 5        | 15 minutes | per user | no        | 14,400       |
| POST_2_dm_conversations_with_param_messages       | 500      | 24 hours   | per app  | no        | 15,000       |
|                                                   | 50       | 24 hours   | per user | no        | 1,500        |
|                                                   | 5        | 15 minutes | per user | no        | 14,400       |
| POST_2_lists                                      | 100      | 24 hours   | per user | no        | 3,000        |
| POST_2_lists_param_members                        | 5        | 15 minutes | per user | no        | 14,400       |
| POST_2_tweets                                     | 100      | 24 hours   | per user | no        | 3,000        |
|                                                   | 1667     | 24 hours   | per app  | no        | 50,010       |
| POST_2_users_id_bookmarks                         | 5        | 15 minutes | per user | no        | 14,400       |
| POST_2_users_param_blocking                       | 5        | 15 minutes | per user | no        | 14,400       |
| POST_2_users_param_followed_lists                 | 5        | 15 minutes | per user | no        | 14,400       |
| POST_2_users_param_following                      | 5        | 15 minutes | per user | no        | 14,400       |
| POST_2_users_param_likes                          | 200      | 24 hours   | per user | no        | 6,000        |
|                                                   | 5        | 15 minutes | per user | no        | 14,400       |
| POST_2_users_param_muting                         | 5        | 15 minutes | per user | no        | 14,400       |
| POST_2_users_param_pinned_lists                   | 5        | 15 minutes | per user | no        | 14,400       |
| POST_2_users_param_retweets                       | 5        | 15 minutes | per user | no        | 14,400       |
| PUT_2_lists_param                                 | 5        | 15 minutes | per user | no        | 14,400       |
| PUT_2_tweets_param_hidden                         | 5        | 15 minutes | per user | no        | 14,400       |

###### 专业

| 请求端点                                          | 请求数量 | 时间窗口   | 请求对象 | 读取权限? | 每个月的限制 |
| ------------------------------------------------- | -------- | ---------- | -------- | --------- | ------------ |
| DELETE_2_lists_param                              | 300      | 15 minutes | per user | no        | 864,000      |
| DELETE_2_lists_param_members_param                | 300      | 15 minutes | per user | no        | 864,000      |
| DELETE_2_tweets_param                             | 50       | 15 minutes | per user | no        | 144,000      |
| DELETE_2_users_id_bookmarks_tweet_id              | 50       | 15 minutes | per user | no        | 144,000      |
| DELETE_2_users_param_blocking_param               | 50       | 15 minutes | per user | no        | 144,000      |
| DELETE_2_users_param_followed_lists_param         | 50       | 15 minutes | per user | no        | 144,000      |
| DELETE_2_users_param_following_param              | 50       | 15 minutes | per user | no        | 144,000      |
| DELETE_2_users_param_likes_param                  | 50       | 15 minutes | per user | no        | 144,000      |
|                                                   | 1000     | 24 hours   | per user | no        | 30,000       |
| DELETE_2_users_param_muting_param                 | 50       | 15 minutes | per user | no        | 144,000      |
| DELETE_2_users_param_pinned_lists_param           | 50       | 15 minutes | per user | no        | 144,000      |
| DELETE_2_users_param_retweets_param               | 50       | 15 minutes | per user | no        | 144,000      |
| GET_2_compliance_jobs                             | 150      | 15 minutes | per app  | no        | 432,000      |
| GET_2_compliance_jobs_param                       | 150      | 15 minutes | per app  | no        | 432,000      |
| GET_2_dm_conversations_param_dm_events            | 100      | 15 minutes | per user | no        | 288,000      |
| GET_2_dm_conversations_with_param_dm_events       | 100      | 15 minutes | per user | no        | 288,000      |
| GET_2_dm_events                                   | 100      | 15 minutes | per user | no        | 288,000      |
| GET_2_lists_id                                    | 75       | 15 minutes | per user | no        | 216,000      |
|                                                   | 75       | 15 minutes | per app  | no        | 216,000      |
| GET_2_lists_id_members                            | 900      | 15 minutes | per user | no        | 2,592,000    |
|                                                   | 900      | 15 minutes | per app  | no        | 2,592,000    |
| GET_2_lists_id_tweets                             | 900      | 15 minutes | per user | yes       | 2,592,000    |
|                                                   | 900      | 15 minutes | per app  | yes       | 2,592,000    |
| GET_2_spaces                                      | 300      | 15 minutes | per user | no        | 864,000      |
|                                                   | 300      | 15 minutes | per app  | no        | 864,000      |
| GET_2_spaces_by_creator_ids                       | 300      | 15 minutes | per user | no        | 864,000      |
|                                                   | 1        | 1 second   | per app  | no        | 2,592,000    |
|                                                   | 1        | 1 second   | per user | no        | 2,592,000    |
|                                                   | 300      | 15 minutes | per app  | no        | 864,000      |
| GET_2_spaces_param                                | 300      | 15 minutes | per app  | no        | 864,000      |
|                                                   | 300      | 15 minutes | per user | no        | 864,000      |
| GET_2_spaces_param_buyers                         | 300      | 15 minutes | per user | no        | 864,000      |
|                                                   | 300      | 15 minutes | per app  | no        | 864,000      |
| GET_2_spaces_param_tweets                         | 300      | 15 minutes | per user | no        | 864,000      |
|                                                   | 300      | 15 minutes | per app  | no        | 864,000      |
| GET_2_spaces_search                               | 300      | 15 minutes | per user | no        | 864,000      |
|                                                   | 300      | 15 minutes | per app  | no        | 864,000      |
| GET_2_tweets                                      | 900      | 15 minutes | per user | yes       | 2,592,000    |
|                                                   | 450      | 15 minutes | per app  | yes       | 1,296,000    |
| GET_2_tweets_counts_recent                        | 300      | 15 minutes | per app  | no        | 864,000      |
| GET_2_tweets_param                                | 900      | 15 minutes | per user | yes       | 2,592,000    |
|                                                   | 450      | 15 minutes | per app  | yes       | 1,296,000    |
| GET_2_tweets_param_liking_users                   | 75       | 15 minutes | per user | no        | 216,000      |
|                                                   | 75       | 15 minutes | per app  | no        | 216,000      |
| GET_2_tweets_param_quote_tweets                   | 75       | 15 minutes | per user | yes       | 216,000      |
|                                                   | 75       | 15 minutes | per app  | yes       | 216,000      |
| GET_2_tweets_param_retweeted_by                   | 75       | 15 minutes | per app  | yes       | 216,000      |
|                                                   | 75       | 15 minutes | per user | yes       | 216,000      |
| GET_2_tweets_search_recent                        | 450      | 15 minutes | per app  | yes       | 1,296,000    |
|                                                   | 300      | 15 minutes | per user | yes       | 864,000      |
| GET_2_tweets_search_stream                        | 50       | 15 minutes | per app  | yes       | 144,000      |
| GET_2_tweets_search_stream_rules                  | 450      | 15 minutes | per app  | no        | 1,296,000    |
| GET_2_users                                       | 300      | 15 minutes | per app  | no        | 864,000      |
|                                                   | 900      | 15 minutes | per user | no        | 2,592,000    |
| GET_2_users_by                                    | 900      | 15 minutes | per user | no        | 2,592,000    |
|                                                   | 300      | 15 minutes | per app  | no        | 864,000      |
| GET_2_users_by_username_param                     | 900      | 15 minutes | per user | no        | 2,592,000    |
|                                                   | 300      | 15 minutes | per app  | no        | 864,000      |
| GET_2_users_by_username_param_followers           | 15       | 15 minutes | per user | no        | 43,200       |
|                                                   | 15       | 15 minutes | per app  | no        | 43,200       |
| GET_2_users_by_username_param_mentions            | 450      | 15 minutes | per app  | no        | 1,296,000    |
|                                                   | 180      | 15 minutes | per user | no        | 518,400      |
| GET_2_users_by_username_param_tweets              | 1500     | 15 minutes | per app  | yes       | 4,320,000    |
|                                                   | 900      | 15 minutes | per user | yes       | 2,592,000    |
| GET_2_users_id_bookmarks                          | 180      | 15 minutes | per user | no        | 518,400      |
| GET_2_users_id_list_memberships                   | 75       | 15 minutes | per app  | no        | 216,000      |
|                                                   | 75       | 15 minutes | per user | no        | 216,000      |
| GET_2_users_id_owned_lists                        | 15       | 15 minutes | per app  | no        | 43,200       |
|                                                   | 15       | 15 minutes | per user | no        | 43,200       |
| GET_2_users_id_pinned_lists                       | 15       | 15 minutes | per user | no        | 43,200       |
|                                                   | 15       | 15 minutes | per app  | no        | 43,200       |
| GET_2_users_me                                    | 75       | 15 minutes | per user | no        | 216,000      |
| GET_2_users_param                                 | 900      | 15 minutes | per user | no        | 2,592,000    |
|                                                   | 300      | 15 minutes | per app  | no        | 864,000      |
| GET_2_users_param_blocking                        | 15       | 15 minutes | per user | no        | 43,200       |
| GET_2_users_param_following_spaces                | 300      | 15 minutes | per user | no        | 864,000      |
|                                                   | 300      | 15 minutes | per app  | no        | 864,000      |
| GET_2_users_param_liked_tweets                    | 75       | 15 minutes | per app  | yes       | 216,000      |
|                                                   | 75       | 15 minutes | per user | yes       | 216,000      |
| GET_2_users_param_mentions                        | 450      | 15 minutes | per app  | yes       | 1,296,000    |
|                                                   | 300      | 15 minutes | per user | yes       | 864,000      |
| GET_2_users_param_muting                          | 15       | 15 minutes | per user | no        | 43,200       |
| GET_2_users_param_timelines_reverse_chronological | 180      | 15 minutes | per user | no        | 518,400      |
| GET_2_users_param_tweets                          | 1500     | 15 minutes | per app  | yes       | 4,320,000    |
|                                                   | 900      | 15 minutes | per user | yes       | 2,592,000    |
| POST_2_compliance_jobs                            | 150      | 15 minutes | per app  | no        | 432,000      |
| POST_2_dm_conversations                           | 200      | 15 minutes | per user | no        | 576,000      |
|                                                   | 2500     | 24 hours   | per app  | no        | 75,000       |
|                                                   | 1000     | 24 hours   | per user | no        | 30,000       |
| POST_2_dm_conversations_param_messages            | 2500     | 24 hours   | per app  | no        | 75,000       |
|                                                   | 1000     | 24 hours   | per user | no        | 30,000       |
|                                                   | 200      | 15 minutes | per user | no        | 576,000      |
| POST_2_dm_conversations_with_param_messages       | 2500     | 24 hours   | per app  | no        | 75,000       |
|                                                   | 1000     | 24 hours   | per user | no        | 30,000       |
|                                                   | 200      | 15 minutes | per user | no        | 576,000      |
| POST_2_lists                                      | 300      | 15 minutes | per user | no        | 864,000      |
| POST_2_lists_param_members                        | 300      | 15 minutes | per user | no        | 864,000      |
| POST_2_tweets                                     | 100      | 15 minutes | per user | no        | 288,000      |
|                                                   | 10000    | 24 hours   | per app  | no        | 300,000      |
| POST_2_tweets_search_stream_rules                 | 100      | 15 minutes | per user | no        | 288,000      |
| POST_2_users_id_bookmarks                         | 50       | 15 minutes | per user | no        | 144,000      |
| POST_2_users_param_blocking                       | 50       | 15 minutes | per user | no        | 144,000      |
| POST_2_users_param_followed_lists                 | 50       | 15 minutes | per user | no        | 144,000      |
| POST_2_users_param_following                      | 50       | 15 minutes | per user | no        | 144,000      |
| POST_2_users_param_likes                          | 1000     | 24 hours   | per user | no        | 30,000       |
|                                                   | 50       | 15 minutes | per user | no        | 144,000      |
| POST_2_users_param_muting                         | 50       | 15 minutes | per user | no        | 144,000      |
| POST_2_users_param_pinned_lists                   | 50       | 15 minutes | per user | no        | 144,000      |
| POST_2_users_param_retweets                       | 50       | 15 minutes | per user | no        | 144,000      |
| PUT_2_lists_param                                 | 300      | 15 minutes | per user | no        | 864,000      |
| PUT_2_tweets_param_hidden                         | 50       | 15 minutes | per user | no        | 144,00       |

###### 企业

定制化


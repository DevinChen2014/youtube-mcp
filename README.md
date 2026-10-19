# YouTube MCP

LobeHub 用户请使用 [LobeHub setup / 接入说明](LOBEHUB.md)，包含专属官网入口、认证和来源配置。

This public listing provides connection metadata and client examples for the hosted SocialDataX YouTube MCP service. The implementation is privately hosted; this directory contains public connection materials only.

<!-- release-status:start -->
## Recorded release status

- Local metadata: `0.1.3` with 12 tracked tools. Local metadata alone does not establish publication.
- Hosted production: `0.1.3` with 12 tools; recorded verification on `2026-10-11 19:32` (Asia/Shanghai).
- Official MCP Registry: `0.1.3` (`active`); recorded verification on `2026-10-11 19:32` (Asia/Shanghai).
- Registry evidence: [version-specific Registry record](https://registry.modelcontextprotocol.io/v0.1/servers/com.52choujiang%2Fyoutube-insights/versions/0.1.3).
- These are recorded observations, not a fresh live check. Public GitHub, npm, and other distribution channels require their own verification.
<!-- release-status:end -->

## Service

- Hosted MCP endpoint: `https://mcp.socialdatax.com/youtube/mcp`
- Hosted transport: `streamable-http`
- Authentication: `Authorization: Bearer <SOCIALDATAX_API_KEY>`
- Product: `SocialDataX` / `社媒数据助手`
- Website and API Key access: <https://socialdatax.com/ai?from=github>
- Registry name: `com.52choujiang/youtube-insights`
- Future registry name: `com.socialdatax/youtube-insights`

## Scope

Use this service for public YouTube channel search, search suggestions, video search and detail, top-level comments, comment replies, channel info, channel video or Shorts lists, and video speech-to-text transcript jobs. It does not provide account login, posting, editing, liking, commenting, following, or other account actions.

## Tools


| Tool | Purpose |
| --- | --- |
| `socialdatax_get_points_balance` | Query the current API Key account's SocialDataX points balance / 积分余额、剩余积分或点数. |
| `youtube_search_channels` | Search channels or creators by keyword; supports page_token. |
| `youtube_search_suggestions` | Get search-box suggestions from a keyword or phrase; returns `items[].text`, without pagination or video/channel details. |
| `youtube_search_videos` | Search public videos; use when a search term is available, and continue with `page_token`. |
| `youtube_get_video_detail_by_url` | Read video details from a video URL. |
| `youtube_get_channel_info_by_url` | Read channel info from a channel URL. |
| `youtube_get_user_posted_videos_by_channel_url` | Read channel videos or Shorts and continue with `page_token`. |
| `youtube_get_video_comments_by_url` | Read first-level comments from a video URL. |
| `youtube_get_video_comment_replies` | Read replies from a `reply_token` and continue with `page_token`. |
| `youtube_submit_video_speech_text_by_url` | Submit a video speech-to-text transcript job from a YouTube video URL. |
| `youtube_submit_video_speech_text_by_video_id` | Submit a video speech-to-text transcript job from an 11-character YouTube `video_id`. |
| `youtube_get_video_speech_text_job` | Check a transcript job by `job_id`; continue until `is_terminal` is true. |

When a video or channel URL is already available, use the corresponding detail, comment, or channel tool instead of searching again.

## Quick Start

Use the hosted endpoint directly when the client supports authenticated `streamable-http`:

```json
{
  "mcpServers": {
    "socialdatax-youtube": {
      "type": "streamable_http",
      "url": "https://mcp.socialdatax.com/youtube/mcp",
      "headers": {"Authorization": "Bearer <SOCIALDATAX_API_KEY>"}
    }
  }
}
```

For command/stdio-only clients, use `npx -y mcp-remote https://mcp.socialdatax.com/youtube/mcp --header "Authorization: Bearer <SOCIALDATAX_API_KEY>"`. See the files in [examples](examples/).

Request or manage API access at <https://socialdatax.com/ai?from=github>. Never commit a real API Key.

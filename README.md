# M3U8 Downloader Product Introduction

## Overview

M3U8 Downloader is a desktop media downloader designed for users who need to browse pages, capture media requests, identify M3U8/MP4 resources, and manage downloads in one place. Built with Electron, it combines an embedded browser, stream sniffing, a download queue, and local file actions for page-based downloads, direct media URLs, live recording, and sources that depend on request headers or session state.

## Core Value

- **Browsing and capture in one app**: open a page and inspect media traffic without switching between a browser and a downloader.
- **Unified queue management**: captured streams, manually pasted URLs, and retry tasks all flow into the same download list.
- **Optimized for streaming media**: detects M3U8, MP4, and related resources, then selects the most suitable download path.
- **Built for harder sites**: preserves page session activity, captures request headers, supports header debugging, and can reopen recovery pages for retry workflows.

## Key Features

### 1. Embedded browsing and stream capture

- Open pages directly inside the app
- Observe page network requests and detect M3U8 or direct media resources
- Switch between desktop, mobile, and custom User-Agent modes
- Keep the browser view alive in the background when leaving the capture page, while muting audio

### 2. Multi-path downloading

The app automatically selects a download strategy based on the resource type and context. Typical fallback flow:

1. Direct download with `ffmpeg`
2. Local proxy + `ffmpeg`
3. Page extraction with `yt-dlp`

Live streams can run as continuous recordings, while standard on-demand media is handled as regular downloads.

### 3. Download queue management

- Track status, progress, speed, ETA, and output details
- Pause, continue, redownload, or record again
- Remove tasks
- Open files and reveal them in the folder
- Inspect full error details
- Reopen a recovery page from a failed task
- Debug request headers for troubleshooting

### 4. Manual task creation

You can add:

- Page URLs
- M3U8 URLs
- Direct media URLs

An optional Cookie field is available for one-off tasks that require session data or temporary authorization.

### 5. Settings and version info

- Configure **FFmpeg M3U8 threads** in Settings
- View the app version in the bottom toolbar
- The update button checks remote metadata, supports in-app download when a platform feed is available, and otherwise falls back to the changelog or manual download page

## Typical Use Cases

- Download HLS / M3U8 video streams from web pages
- Capture real media requests from an embedded browser
- Manage multiple download tasks in one queue
- Record live streams
- Troubleshoot downloads affected by headers, cookies, or User-Agent differences

## Platform and Dependencies

- Packaged for macOS, Windows, and Linux
- Depends on bundled `ffmpeg` and `yt-dlp` binaries
- Binaries are organized under `resources/bin/<platform>-<arch>/`

## Notes

- Not every site can be captured or downloaded successfully. Results depend on site behavior, login state, region restrictions, and anti-bot controls.
- In-app updates depend on the update JSON including platform-specific feed information.
- Some advanced options are still experimental and may have different effects across sites.

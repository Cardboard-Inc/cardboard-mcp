# Cardboard

Cardboard is an AI video editor you use from Claude or ChatGPT. Bring in your footage, say what you want in plain
words, and every edit plays in the chat. When it looks right, export the finished video.

This repo holds Cardboard's plugin: the address of Cardboard's hosted MCP server, the Cardboard skill that tells the
assistant how to edit, and the manifests Claude and ChatGPT read. Cardboard runs the server; its code isn't in this repo.

## Server URL

```text
https://mcp.cardboard.ai/mcp
```

Streamable HTTP, with OAuth sign-in. You need a Cardboard account: sign up at [cardboard.ai](https://www.cardboard.ai).

## Connect

### ChatGPT

From ChatGPT's plugins:

1. In ChatGPT, open **Plugins** and find **Cardboard**.
2. Choose **Connect**, sign in to your Cardboard account, and allow ChatGPT access.
3. In a chat, type `@Cardboard`, pick it, and ask for an edit.

Or as a custom MCP server: open **Plugins**, then **Add**, then **Add custom MCP server**. Name it **Cardboard**, enter
the server URL, and choose **Create**, then **Connect**. Depending on your plan, this may need developer mode, or an
admin to allow it for your workspace.

### Claude

Install the plugin from this repo, which adds the Cardboard skill and connector together:

1. In Claude, open **Customize**, then **Plugins**, then **Add**, then **Add marketplace**.
2. Choose **Add from a repository**, enter `Cardboard-Inc/cardboard-mcp`, and choose **Sync**.
3. Open **Cardboard** in the list and choose **Add**.
4. On the plugin's **Connectors** tab, choose **Connect**. Sign in to your Cardboard account and allow Claude access.
5. In a chat, ask for an edit.

Or as a custom connector: open **Customize**, then **Connectors**, then **Add custom connector**. Name it **Cardboard**,
enter the server URL, and choose **Add**, then **Connect**. On Team and Enterprise plans, an owner may need to add it for
the organization first.

## What you can do

- Upload clips and photos from your computer or phone, or bring in a video from a link.
- Cut, trim and reorder clips; remove pauses and filler words; find the moment someone said something.
- Add captions, titles, music, sound effects and a voiceover.
- Change the look with a color grade, or cut a person out of the background.
- Start from a recipe: a finished edit by Cardboard's team that turns your footage into that kind of video.
- Watch every edit play in the chat, and undo any change.
- Export the finished video as an MP4.

Projects are saved to your Cardboard account, so you can pick one up in a later chat. What you can do also depends on
your plan; see [plans and pricing](https://www.cardboard.ai/pricing).

## Tools

The assistant calls these. Tools marked "Uses credits" draw on your plan's credits.

**Projects**

| Tool             | What it does                                                                           |
| ---------------- | -------------------------------------------------------------------------------------- |
| `list_projects`  | Lists your Cardboard projects, most recently edited first.                             |
| `create_project` | Creates a new, empty project.                                                          |
| `show_projects`  | Shows your projects in a card in the chat, where you can search them and pick one.     |
| `project_status` | Tells the assistant how uploads, edits, previews and exports went, and why one failed. |
| `account_usage`  | Shows your plan and what it has left: exports, usage and credits.                      |

**Recipes**

| Tool           | What it does                                                                            |
| -------------- | --------------------------------------------------------------------------------------- |
| `show_recipes` | Shows Cardboard's recipes in a card in the chat, where you can watch them and pick one. |
| `start_recipe` | Makes a new project from a recipe, with your answers to its questions.                  |
| `read_recipe`  | Reads a file of the recipe a project was started from, such as its brief.               |

**Timeline**

| Tool               | What it does                                                                                  |
| ------------------ | --------------------------------------------------------------------------------------------- |
| `print_timeline`   | Reads a project's timeline: its clips, titles and timings.                                    |
| `check_timeline`   | Shows what an edit would change, without changing anything.                                   |
| `apply_timeline`   | Edits the timeline: cuts, trims, order, titles and look. Each edit is a version you can undo. |
| `verify_timeline`  | Checks the timeline for problems such as gaps, overlaps, text off screen or missing media.    |
| `timeline_history` | Lists the saved versions of the timeline, newest first.                                       |
| `undo_timeline`    | Goes back to the previous version of the timeline, or to an earlier saved one.                |
| `look`             | Shows the assistant frames of the edit as the player draws them, to check its work.           |

**Media**

| Tool               | What it does                                                                                   |
| ------------------ | ---------------------------------------------------------------------------------------------- |
| `upload_media`     | Opens an upload card in the chat, where you pick video, audio or photo files on your device.   |
| `add_media`        | Adds the video, audio and photo files you attach to a ChatGPT chat to a project. ChatGPT only. |
| `list_media`       | Lists the files in a project and whether each one is present.                                  |
| `download_media`   | Brings in what a link points at: the video behind a post, or a video, audio or image file.     |
| `capture_web_page` | Takes a screenshot of a web page and adds it to a project.                                     |
| `search_footage`   | Finds stock, archival and YouTube clips for a shot, with links to bring them in.               |
| `search_music`     | Finds tracks in Cardboard's music library by mood, genre or feel.                              |
| `search_sfx`       | Finds sound effects in Cardboard's library, such as whooshes, hits and clicks.                 |
| `probe_media`      | Reads a file's details: length, size, frame rate and audio.                                    |
| `grab_frame`       | Shows the assistant one frame of a video or photo.                                             |
| `filmstrip`        | Shows the assistant evenly spaced frames of a video in one image.                              |
| `detect_scenes`    | Finds the shot changes in a video.                                                             |
| `matte_media`      | Separates a person or the main subject from the background of a video or photo. Uses credits.  |

**Audio and speech**

| Tool                      | What it does                                                                           |
| ------------------------- | -------------------------------------------------------------------------------------- |
| `waveform_image`          | Draws a file's audio as an image.                                                      |
| `waveform_levels`         | Measures audio levels across a file, to find quiet parts, beats or the loudest moment. |
| `detect_silence`          | Finds the silent stretches in a file's audio.                                          |
| `measure_loudness`        | Measures how loud a file is, to even out audio.                                        |
| `transcribe_media`        | Transcribes the speech in a video or audio file, with a time for each word.            |
| `search_transcript`       | Finds a phrase in a project's transcripts, and when it is spoken.                      |
| `caption_from_transcript` | Builds captions for the timeline from its transcripts.                                 |

**Generation**

| Tool                | What it does                                                                        |
| ------------------- | ----------------------------------------------------------------------------------- |
| `generate_video`    | Makes a video clip from a description and places it on the timeline. Uses credits.  |
| `generate_image`    | Makes a still image from a description and places it on the timeline. Uses credits. |
| `generation_status` | Waits for a video or image being made, and fills its place on the timeline.         |
| `generate_voice`    | Reads a script aloud in a chosen voice and places it on the timeline. Uses credits. |
| `generate_music`    | Makes an instrumental music track and places it on the timeline. Uses credits.      |
| `generate_sfx`      | Makes a sound effect and places it on the timeline. Uses credits.                   |
| `list_voices`       | Lists your account's voices: favourites, recent ones and clones.                    |
| `search_voices`     | Searches the library of voices a voiceover can use.                                 |

**Preview and export**

| Tool           | What it does                                                            |
| -------------- | ----------------------------------------------------------------------- |
| `show_preview` | Opens a player in the chat on a project's latest preview.               |
| `export_video` | Exports the finished video. The player in the chat offers the download. |
| `job_status`   | Waits for a long task, such as an export, and returns its result.       |
| `cancel_job`   | Stops a running task. A stopped export leaves no file.                  |

**Help**

| Tool            | What it does                                                                                     |
| --------------- | ------------------------------------------------------------------------------------------------ |
| `docs`          | Reads Cardboard's editing guide, which the assistant follows while it edits.                     |
| `send_feedback` | With your yes, sends Cardboard's team a bug report or feature request, with your name and email. |

## Sign-in and permissions

The assistant signs in with OAuth at `accounts.cardboard.ai` and never sees your Cardboard password. It asks for two
permissions:

| Permission       | What it allows                                                           |
| ---------------- | ------------------------------------------------------------------------ |
| `cardboard:read` | Listing your projects and media, and looking at them.                    |
| `cardboard:edit` | Changing projects, uploading, exporting, and anything that uses credits. |

The connector works only on the projects you make with it. To take access back, disconnect or remove Cardboard in
Claude's **Customize › Connectors** or ChatGPT's **Plugins**.

## Data and privacy

Cardboard sees the tool calls the assistant makes, not your conversation. Your uploads, projects and exports are kept
while your Cardboard account is open. See [data handling](https://docs.cardboard.ai/mcp/data), the
[Privacy Policy](https://www.cardboard.ai/privacy) and the [Terms of Service](https://www.cardboard.ai/terms).

## What's in this repo

| Path                           | What it is                                                                          |
| ------------------------------ | ----------------------------------------------------------------------------------- |
| `skills/cardboard/`            | The Cardboard skill: how the assistant edits with Cardboard                         |
| `.claude-plugin/`, `.mcp.json` | The plugin and marketplace in Claude's format                                       |
| `plugin.json`, `mcp.json`      | The same plugin in OpenAI's format, as ChatGPT's directory lists it                 |
| `server.json`                  | The server's entry for the [MCP Registry](https://registry.modelcontextprotocol.io) |
| `assets/logo.png`              | Cardboard's logo                                                                    |

The files are copied from Cardboard's own repo at each release, so we don't take pull requests here.

## Help

- Docs: [docs.cardboard.ai](https://docs.cardboard.ai/mcp)
- Support: [support@cardboard.ai](mailto:support@cardboard.ai)
- Security issues: see [SECURITY.md](SECURITY.md)

## License

The files in this repo are under the [Apache License 2.0](LICENSE). The license doesn't cover the Cardboard service, or
the Cardboard name and logo.

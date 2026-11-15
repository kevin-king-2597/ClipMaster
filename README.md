# ClipMaster

An open-source AI agent that turns a long video into ranked, captioned short clips.

> 🚧 Work in progress: being built over five evenings.

## How it works

1. **Long video in:** an MP4 file or a URL.
2. **Transcribe:** faster-whisper (runs locally) produces a transcript with word-level timestamps.
3. **Find highlights:** an LLM ranks candidate moments (start, end, hook line, score, reason).
4. **Check boundaries:** a second LLM pass fixes mid-sentence cuts and retries bad clips.
5. **Cut and caption:** FFmpeg cuts each clip, crops to 9:16 and burns in subtitles.
6. **Clips out:** ranked clips plus a cost report per video.

Steps 3 and 4 are what make this an agent rather than a script.

## Stack

| Part | Choice |
| --- | --- |
| Transcription | faster-whisper |
| LLM | Claude or OpenAI API |
| Agent loop | LangGraph |
| Video | FFmpeg |
| Interface | CLI, then an MCP server |

## Roadmap

- [ ] Evening 1: video ingest, audio extraction, transcription
- [ ] Evening 2: highlight prompt, structured output, cost logging
- [ ] Evening 3: FFmpeg cut, 9:16 crop, captions
- [ ] Evening 4: LangGraph boundary check and retry, MCP server
- [ ] Evening 5: mini eval, demo video

## License

MIT

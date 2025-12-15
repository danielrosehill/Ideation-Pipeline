# Vibe Coding Ideas Pipeline 

The purpose of this repository is providing an organized workspace for holding ideas for projects that can be vibe coded as utilities. 

The general workflow is as noted in REAME:

- Ideas were captured as audio files.
- There they are transcribed (MCP or local Whisper) into a `transcripts/` subfolder
- The raw transcript is refined (always as a separate version to preserve the raw original)
- AI analysis assessments are generated into an `ai-analysis/` subfolder
- Finally a spec is developed from that

Once the audio has been transcribed and the derivative documents are generated, the folder should be maintained with the following structure:
- Audio files (root of idea folder)
- `transcripts/` - Raw and refined transcripts
- `ai-analysis/` - AI-generated assessments (does-it-exist, ratings, etc.)
- Specification documents (root of idea folder)

It is intentional that the audio files are deliberately committed to version control and publicly accessible in the repository. 

Sometimes I might request that the audio file be edited, likely to remove silences with a script. In that case, the original can be disposed of, but the edited version should be maintained as it contains context data that may not have been captured 100 percent in the transcripts. 

As a repository grows, common ideas can be grouped into folders.  I will also implement a system for marking the progress. 

Finally, the date should always be recorded in the transcript. If the date is not returned by the MCP as it usually will not be then added to the top of all the transcripts that are generated
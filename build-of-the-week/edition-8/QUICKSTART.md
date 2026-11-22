# Build of the Week — Edition 8: Dictate Anywhere, With Nothing Leaving Your Machine

**Tool:** anomalyco/hex — https://github.com/anomalyco/hex
**License:** MIT
**Budget:** Under one hour
**What you get:** Local voice dictation on Mac, Windows, and Linux. Hold a key, speak, and the text pastes into the app you are in. After the first download, no speech leaves your machine.

## What you need

- A Mac (Apple silicon), a Windows PC (x64 or ARM64), or a Linux machine (x86_64 or ARM64).
- A microphone. The built-in one is enough for a first test.
- Disk space for one speech model, downloaded on the first run.

## Steps

1. **Install Hex.** Use one route:
   - Mac (Homebrew): `brew install --cask anomalyco/tap/hex`
   - Linux (install script): `curl -fsSL https://anoma.ly/hex/install-linux.sh | sh`
   - Linux (AUR): `yay -S hex-bin`
   - Linux (Nix): `nix profile add github:anomalyco/hex`
   - Windows or Mac without Homebrew: download the installer or DMG from the repo's Downloads table.

2. **Run it once and let it download its speech model.** On an English system the default is Parakeet Unified English, which writes while you talk. After this download, transcription stays on your device.

3. **Give it the names it must get right.** Open the Vocabulary list and add your customer names, product names, and part numbers. Whisper and Qwen3-ASR models read the list while they transcribe.

4. **Dictate one real email.** Open your mail app, click in the message body, hold the shortcut, speak the email, and release. Read the pasted text before you send — check names and numbers first.

5. **Dictate one real note.** Repeat in your notes app or a document. Use the Tap mode (Shortcut mode in settings) if you prefer to start and stop with a press instead of holding the key.

6. **Check the record.** History keeps your dictations, searchable, for 7 days by default. Press Option-Shift-V (Ctrl-Alt-V on Windows and Linux) to paste the last dictation again.

## Notes and cautions

- The project does not take pull requests; report bugs or ideas as issues on the repo.
- Other speech models are in the settings picker (for example Whisper large-v3-turbo for many languages, Parakeet v3 for 25 European languages). A bigger model is a bigger download.
- Meetings transcription and Annotate are Labs features on macOS; keep them off for a first run.
- From the command line, `hex transcribe meeting.m4a` prints a recording's transcript whether or not the app is running.

## Source

README, install routes, and speech-model list read on the repo page, Nov 22, 2026: https://github.com/anomalyco/hex

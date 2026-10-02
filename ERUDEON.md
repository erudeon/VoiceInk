# erudeon's fork of VoiceInk

This is erudeon's fork of [Beingpax/VoiceInk](https://github.com/Beingpax/VoiceInk), kept as our own dictation app in place of Wispr Flow. It stays GPL v3 like the original. `upstream` is Beingpax/VoiceInk; `origin` is erudeon/VoiceInk.

How we run it: Parakeet V3 transcribes on the Mac, a cheap cloud model does the cleanup (brackets, quotes, lists), and VoiceInk Refine, the app's own local cleanup model, takes over whenever the cloud fails.

## What we changed

| Change | Why |
| :--- | :--- |
| A failed cloud cleanup falls back to VoiceInk Refine at once, without retries | A slow or offline cloud model must never stall a dictation; before, it retried up to three times and then pasted the raw text |

Build it with `make local` (needs cmake and Xcode's Metal toolchain: `brew install cmake`, `xcodebuild -downloadComponent MetalToolchain`).

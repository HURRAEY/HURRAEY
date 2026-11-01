<p>
  <img src="./assets/terminal.svg" alt="HURRAEY - Audio Software Engineer. DAWs and audio editing tools for web and desktop." width="100%" />
</p>

### `$ ls libraries/`

#### [daw-engine](https://github.com/HURRAEY/daw-engine) · TypeScript audio editing library

I built **daw-engine** independently to provide a reusable foundation for multitrack audio editors. It was later adopted in AnAI's media editors to share editing logic across products.

Audio playback is one part of an editor. Tracks, clip placement, undo/redo, routing, and saved projects also need to stay consistent as users edit. daw-engine brings these responsibilities into a shared editing core.

- **Non-destructive editing** - Keep source audio separate from timeline regions. Moving, splitting, and trimming clips changes references and timing data rather than copying or modifying the original audio.
- **Commands and history** - Route editing operations through executable, undoable commands so different UI inputs can share the same editing behavior.
- **Backend adapters** - Separate editing logic from audio playback and rendering. Applications connect their own audio backends through adapters and provide the UI.
- **Shared project model** - Manage tracks, mixer routing, automation data, and serializable project snapshots, with utilities for Canvas-based timelines, waveforms, and virtual scrolling.

[Source](https://github.com/HURRAEY/daw-engine) · [Core](https://github.com/HURRAEY/daw-engine/tree/main/core) · [Timeline UI utilities](https://github.com/HURRAEY/daw-engine/tree/main/ui-utils)

#### [@hurraey/video-thumbnail](https://www.npmjs.com/package/@hurraey/video-thumbnail) · Video timeline thumbnails

A framework-independent TypeScript library that prioritizes thumbnails currently visible in the timeline.

- **Three-stage generation** - Display a poster fallback first, seek visible timestamps with `HTMLVideoElement`, and backfill non-visible frames with Web Workers and WebCodecs.
- **Viewport-aware scheduling** - Discard stale results after scrolling or zooming, prefer requested-time frames over coarse background frames, and release resources when a source is removed.

[npm package](https://www.npmjs.com/package/@hurraey/video-thumbnail)

#### [Timeline virtualization](https://github.com/HURRAEY/daw-engine/tree/main/ui-utils#track-layout-and-virtual-scroll) · daw-engine UI utilities

Reusable TypeScript tools for rendering the visible portion of a DAW timeline, included in `@daw-engine/ui-utils`.

- **Visible items and overscan** - Calculate which items to render, with support for variable item sizes, cached offsets, and binary search for the first visible item.
- **Rendering stays in the application** - Return item positions and spacer sizes without depending on a UI framework. Combine with track layout and viewport utilities for scrolling and zooming.

[Documentation](https://github.com/HURRAEY/daw-engine/tree/main/ui-utils) · [VirtualScroll source](https://github.com/HURRAEY/daw-engine/blob/main/ui-utils/src/scroll/VirtualScroll.ts)

### `$ cat contributions.md`

Selected contributions across my [HURRAEY](https://github.com/HURRAEY) and [whizzkid1452](https://github.com/whizzkid1452) accounts.

#### React Native & React DevTools

- **[React Native #57558](https://github.com/react/react-native/pull/57558) · Merged via Meta's code sync** - Fixed an Android `ClassCastException` when numeric `outlineColor` values reached a view manager without color conversion, and added a regression test.
- **[React DevTools #37017](https://github.com/react/react/pull/37017) · Open PR** - Handle Profiler import file-read failures with the existing error dialog instead of leaving users without feedback. Reuse the dialog logic and add regression coverage.

#### TanStack

- **[Query #11013](https://github.com/TanStack/query/pull/11013) · Merged** - Added tests for query-key equality with `undefined` properties and timeout validation boundary cases.
- **[tanstack.com #1021](https://github.com/TanStack/tanstack.com/pull/1021) · Open PR** - Improve search-dialog input focus on initial open and reopen while preserving focus intentionally moved to another control.

#### Tone.js

- **[#1458](https://github.com/Tonejs/Tone.js/pull/1458) · Merged** - Preserved a scheduled source start time when the native audio node is created after a suspended `AudioContext` resumes, with regression coverage.
- **[#1453](https://github.com/Tonejs/Tone.js/pull/1453) · Merged** - Removed focused-test modifiers and corrected audio-gate assertions. The maintainer's [follow-up safeguard against focused tests (#1454)](https://github.com/Tonejs/Tone.js/pull/1454) acknowledges my report.

#### Web Audio API specification

- **[#2684](https://github.com/WebAudio/web-audio-api/pull/2684) · Open PR** - Clarify resource acquisition for `AudioContext.setSinkId()` so it uses the requested output target, including silent output.
- **[#2682](https://github.com/WebAudio/web-audio-api/pull/2682) · Merged** - Corrected the Git attributes filename so the repository's text and line-ending settings take effect.
- **[#2683](https://github.com/WebAudio/web-audio-api/pull/2683) · Merged** - Corrected typos and formatting in the contribution guide.


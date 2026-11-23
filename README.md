# shared-assets

Shared files used by different tools and software, and unchanged backup copies of some
public libraries and models. Every file keeps its original name and stays under its own
licence, which is published with it.

## How it is organised

- **[index.json](index.json)** lists every collection and file: size, SHA-256, licence and
  where to download it, best source first (usually the original publisher, then this
  repository's release). Programs read it from
  `https://raw.githubusercontent.com/adityamilan/shared-assets/main/index.json`.
- **Releases**: each collection is one release, its tag is the collection name
  (`<name>-v<N>`). Files are downloaded from
  `https://github.com/adityamilan/shared-assets/releases/download/<collection>/<file>`.
  A published release is never changed; new or updated files go into a new collection
  (`<name>-v<N+1>`), so programs relying on an older one keep working.
- **On the computer**, programs keep downloaded files in one shared folder,
  `%LOCALAPPDATA%\Milansoft\shared-assets\<collection>\`, so a file one program has
  downloaded is not downloaded again by another. The last index read is kept there too.

## Rules for programs using it

1. Download only when the user asks for the feature, saying how much and asking first.
2. Look in the shared folder first.
3. Take the sources from index.json in order; `{"release": true}` means this repository's
   release of the collection.
4. Check each file's SHA-256 (programs should also carry the SHA-256 of the files they
   expect, so a changed index can't hand them other files); download to `<file>.part` and
   rename when it matches.
5. Don't delete the shared folder on uninstall; remove files only when the user asks.

## Collections

| Collection | Contents |
|---|---|
| [image-ai-v1](https://github.com/adityamilan/shared-assets/releases/tag/image-ai-v1) | Image upscaling (Real-ESRGAN general x4v3, 4xNomos8kSC), face detection (YuNet) and face restoration (RestoreFormer++) models, and ONNX Runtime 1.24.4 with DirectML (Windows x64) |

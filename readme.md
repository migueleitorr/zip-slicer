# Zip Slicer

A lightweight, client-side web application for splitting large `.tgz`, `.tar.gz`, `.tar`, and `.zip` archives into smaller, standalone parts directly in the browser.

[![Live Demo](https://img.shields.io/badge/demo-GitHub%20Pages-3b82f6)](https://migueleitorr.github.io/zip-slicer/)
[![License: MIT](https://img.shields.io/badge/License-MIT-10b981.svg)](LICENSE)

## Overview

Many cloud platforms, web portals, and analysis tools enforce strict file size, uncompressed payload, or file count limits on uploaded archives. **Zip Slicer** solves this by repartitioning large archives into smaller, independently valid archive parts without uploading any data to an external server.

Unlike raw binary splitters that produce unusable file fragments (`.part01`, `.part02`) requiring command-line reassembly, Zip Slicer generates **standalone archives** (`_part01.tgz`, `_part02.tgz`, or `.zip`) that can be opened, extracted, or uploaded individually.

## Features

- **100% Client-Side Privacy:** Powered by the browser's native `File`, `Blob`, and `CompressionStream` / `DecompressionStream` Web APIs. Files never leave your machine.
- **Standalone Output Parts:** Every generated part has valid headers, checksums, and directory structures so it can be extracted independently.
- **Configurable Thresholds:**
  - **Max Part Size (MB):** Cap the compressed file size of each generated part (10 MB – 60 MB).
  - **Max Uncompressed (MB):** Cap the total uncompressed payload inside each part (40 MB – 220 MB).
  - **Max Files per Part:** Limit the number of internal files packaged into a single part (100 – 1,000 files).
- **Multiple Output Formats:**
  - **Standalone `.tgz` Parts:** Standard POSIX USTAR `.tgz` archives.
  - **Standalone `.zip` Parts:** Standard `.zip` archives with verified CRC-32 checksums.
  - **Text Bundles (`.txt`):** Consolidated plain-text bundles for workflows that only accept `.txt` files.
- **Automatic Content Normalization:**
  - Unpacks nested `.gz`, `.tgz`, and `.tar` archives inline.
  - Preserves symbolic and hard links in an internal `ARCHIVE_MANIFEST.txt` summary.
  - Extracts printable strings from binary files into readable `.strings.txt` files.
  - Sanitizes file paths to strictly conform to POSIX USTAR specifications.
- **Zero Dependencies:** Built with vanilla HTML, CSS, and JavaScript in a single `index.html` file.

## How to Use

1. Open the [Live Application](https://migueleitorr.github.io/zip-slicer/) (or open `index.html` locally in your browser).
2. Drag and drop a `.tgz`, `.tar.gz`, `.tar`, or `.zip` archive into the upload area, or click to browse.
3. *(Optional)* Adjust the **Max Part Size**, **Max Uncompressed**, **Max Files per Part**, or **Output Format** controls.
4. Click **Split Archive**.
5. Download individual parts or click **Download All**.

## Running Locally

Because Zip Slicer is a static single-file application with no build step or external dependencies, you can run it directly on your computer:

```bash
git clone [https://github.com/migueleitorr/zip-slicer.git](https://github.com/migueleitorr/zip-slicer.git)
cd zip-slicer
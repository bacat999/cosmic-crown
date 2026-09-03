---
name: Runtime file reads vs esbuild bundle
description: Libraries that read asset files from their own package dir break in the bundled API server
---

# Libraries reading package-dir files break under the esbuild bundle

The API server ships as a single esbuild bundle. Any dependency that reads an asset file from its own package directory at runtime (e.g. connect-pg-simple's `table.sql` for `createTableIfMissing`) fails silently or with ENOENT under `dist/`.

**Why:** the bundle contains only JS; package-relative asset paths no longer resolve.

**How to apply:** provision such assets ourselves (e.g. required DDL in the server's runtime migrations) and disable the library's file-reading option. When something "silently doesn't work" only in the bundled server, suspect this first.

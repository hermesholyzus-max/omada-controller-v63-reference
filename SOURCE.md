# Source material and local verification

The original TP-Link manual is intentionally excluded from this portable distribution. Retain it in the existing document store; this package should contain only the paraphrased reference notes.

## Optional relative local layout

To verify source pages locally without relying on a machine-specific path, copy or link the original file to:

`source/Omada SDN Controller_V6.3_User Guide.pdf`

The `source/` directory is ignored by Git and must not be uploaded as part of this distribution.

## Expected source identity

- File name: `Omada SDN Controller_V6.3_User Guide.pdf`
- Cover revision: `REV6.3.0`
- Copyright line: `© 2026 TP-Link`
- Physical PDF pages: `521`
- SHA-256: `e28ed7b66306f204a63e9624355afb0c723c27b9aee6b5e7b260207ece155ed9`

Example verification from this package root:

`sha256sum "source/Omada SDN Controller_V6.3_User Guide.pdf"`

A matching hash confirms the exact manual used when these notes were prepared. The notes cite **physical PDF pages**. For printed body pages 2–510, the checked relationship is `PDF page = guide page + 11`.

## Distribution boundary

Do not upload the PDF, controller backups, support bundles, device exports, credentials, private keys, or tokens to GitHub. The existing document-store copy remains the source of record.

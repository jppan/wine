# Licensing of this Wine fork (LGPL branch `madeira-lgpl`)

This repository is a fork of [Wine](https://www.winehq.org/), which upstream
distributes under **LGPL-2.1-or-later**. This branch keeps that licence.

- Upstream code: LGPL-2.1-or-later, all upstream copyright and licence
  notices unchanged. Baseline: upstream tag `wine-11.4`.
- Modifications and new files authored for
  [Madeira](https://github.com/willfaust/Madeira): **LGPL-2.1-or-later**,
  Copyright (C) 2026 Will Faust, except the third-party contributions
  listed below. The new `dlls/wineios.drv` files are
  derived from upstream `winecoreaudio.drv` and keep its CodeWeavers and
  Huw Davies copyright notices.
- Provenance: the branch was rebuilt from the upstream baseline with the 51
  commits listed in the Madeira repository's `docs/wine-lgpl-provenance.md`,
  cherry-picked from the earlier GPL-converted branch with `-x` (each commit
  message names its origin). Later changes are committed on this branch
  directly. The earlier branch's LGPL-section-3 conversion to
  GPL-3.0 is NOT applied here; that conversion is irreversible for that
  copy, which is why this branch was rebuilt from the upstream baseline
  instead.
- Third-party contributions, **LGPL-2.1-or-later**, copyright retained by
  their authors, each signed off under the DCO (see `CONTRIBUTING.md`):
  - `feb96ad2be4` xinput: read Madeira host controller snapshots through
    win32u. Author: 125hz. Merged from pull request #1 on 2026-09-25.
  - opengl32: OpenGL ES contexts for Madeira's winios WGL driver
    (`dlls/opengl32/unix_wgl.c`), the fixed low image base limited to x86
    builds (`dlls/opengl32/Makefile.in`), and the `[park-5s]` stuck-wait
    report (`dlls/ntdll/unix/sync.c`). Author: Connor Gow, written with AI
    assistance, 2026-09-26. Carried as patches in the Madeira repository
    (`patches/wine-opengl-winios.patch`, `patches/wine-ntdll-park-report.patch`).
  - opengl32: 32-bit (WoW64) callers on iOS. `make_opengl` makes the wow64
    thunks convert embedded guest pointers with `ios_wow_host_ptr()`, keeps
    handles and callbacks unchanged, and passes pointer-or-offset parameters
    unchanged while a buffer is bound (`dlls/opengl32/make_opengl`,
    regenerated `unix_thunks.c`, `unix_private.h`, `unix_wgl.c`). Author:
    Connor Gow, written with AI assistance, 2026-09-27. Carried in
    `patches/wine-opengl-winios.patch`.

The LGPL permits combining this library with proprietary components (such
as Apple's Metal Shader Converter) subject to LGPL-2.1 section 6; see the
Madeira repository's `docs/LICENSING.md`.

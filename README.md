# FF14 Mobile Reverse Archive

Unofficial research archive for Final Fantasy XIV Mobile analysis, documentation, and resource references.

本项目用于整理《FF14：水晶世界》手游的研究资料、客户端静态分析记录、工具索引和社区资源参考。项目与 Square Enix、腾讯或其他相关权利人没有官方关联。

## Contents

- `00-docs/`: Offline copies of relevant documentation and reference pages.
- `01-apk/`: Local APK research inputs. Large files excluded from Git history may be available separately.
- `02-client-backup/`: Local client backup files and extracted resource archives.
- `03-tools/`: Tool archives and reference source used during local analysis.
- `04-apk-analysis/`: APK extraction and static-analysis output.
- `08-community-reference/`: Community resource references and sample files.
- `FF14-Mobile-Resources.md`: Research notes, source links, and resource index.
- `Release-Assets/`: Local-only staging directory for GitHub Release attachments; it is intentionally excluded from Git.

## GitHub Release Assets

Some large files cannot be stored in the Git repository and are prepared as Release attachments instead. The client ZIP is split into nine raw binary parts:

```text
com.tencent.tmgp.fmgame.zip.part.01
com.tencent.tmgp.fmgame.zip.part.02
com.tencent.tmgp.fmgame.zip.part.03
com.tencent.tmgp.fmgame.zip.part.04
com.tencent.tmgp.fmgame.zip.part.05
com.tencent.tmgp.fmgame.zip.part.06
com.tencent.tmgp.fmgame.zip.part.07
com.tencent.tmgp.fmgame.zip.part.08
com.tencent.tmgp.fmgame.zip.part.09
```

On Windows, place all parts in one directory and run this command in Command Prompt:

```cmd
copy /b com.tencent.tmgp.fmgame.zip.part.01+com.tencent.tmgp.fmgame.zip.part.02+com.tencent.tmgp.fmgame.zip.part.03+com.tencent.tmgp.fmgame.zip.part.04+com.tencent.tmgp.fmgame.zip.part.05+com.tencent.tmgp.fmgame.zip.part.06+com.tencent.tmgp.fmgame.zip.part.07+com.tencent.tmgp.fmgame.zip.part.08+com.tencent.tmgp.fmgame.zip.part.09 com.tencent.tmgp.fmgame.zip
```

Verify the reconstructed ZIP with `SHA256SUMS.txt`. The expected SHA-256 is:

```text
39365DD1A451391F7E6A58DF513F419760C44E5A4F721525E7800D4081D25866
```

The parts are raw binary splits, not a 7-Zip multi-volume archive. They must be concatenated in numerical order before opening the reconstructed ZIP.

## Research Boundaries

This archive is intended for lawful local archival, interoperability, and static-analysis research. Do not use the materials to access services without authorization, bypass account or platform security, or handle account tokens, cookies, credentials, or other sensitive data.

Before downloading, using, or redistributing any file, review the applicable copyright, license, and distribution terms. Game software and assets belong to their respective owners. Tool archives and community resources remain subject to their original licenses and author permissions.

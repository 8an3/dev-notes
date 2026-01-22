 
<!-- #region HEADER -->

<div align="center">

![Z](https://raw.githubusercontent.com/8an3/dev-notes/main/utils/5.gif)

</div>
<p align="center"><h1 align="center">DevStack</h1></p>
<p align="center"><em>The Extension That Fixed VSCode</em></p>
<p align="center">TLDR:<p>


| 🚀 **FIRST-IN-CATEGORY** · <i>Exclusive Innovations</i> | 🏆 **BEST-IN-CATEGORY** · <i>Superior Workflow Tools</i> |
|:-------------------------|:-------------------------|
| **<a href="https://github.com/8an3/dev-notes/blob/main/docs/LOKI.md"  style="font-size: 12px;"><img src="https://img.shields.io/badge/LOKI-0284c7?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij4KPHBhdGggZD0iTTAgMCBDNC43ODA4OTg4NCAxLjkxMjM1OTU0IDYuNzA3MzQ3NiAzLjIzNjk2ODY5IDEwIDcgQzEwIDcuNjYgMTAgOC4zMiAxMCA5IEM3LjA4NDgyNzA4IDcuOTI1OTg4OTIgNS4yMjE4OTgyNCA3LjIyMTg5ODI0IDMgNSBDMi42NyAxMC42MSAyLjM0IDE2LjIyIDIgMjIgQzEuMzQgMjIgMC42OCAyMiAwIDIyIEMwIDE0Ljc0IDAgNy40OCAwIDAgWiAiIGZpbGw9IiMwMDAwMDAiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDcsMSkiLz4KPC9zdmc+Cg==" valign="middle"></a> Operate AI outside the data set**<br><span style="font-size: 12px;">- Shapeshifter - adapts prompts dynamically<br>- Rule breaker - bypasses AI limitations and training constraints<br>- Trickster - manipulates the system cleverly<br>- Boundary crosser - transcends what the base model can do<br>- Chaos agent - creates novel solutions outside training data </span> | **<a href="https://github.com/8an3/dev-notes/blob/main/docs/LOKI.md" style="font-size: 12px;"><img src="https://img.shields.io/badge/LOKI-0284c7?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij4KPHBhdGggZD0iTTAgMCBDNC43ODA4OTg4NCAxLjkxMjM1OTU0IDYuNzA3MzQ3NiAzLjIzNjk2ODY5IDEwIDcgQzEwIDcuNjYgMTAgOC4zMiAxMCA5IEM3LjA4NDgyNzA4IDcuOTI1OTg4OTIgNS4yMjE4OTgyNCA3LjIyMTg5ODI0IDMgNSBDMi42NyAxMC42MSAyLjM0IDE2LjIyIDIgMjIgQzEuMzQgMjIgMC42OCAyMiAwIDIyIEMwIDE0Ljc0IDAgNy40OCAwIDAgWiAiIGZpbGw9IiMwMDAwMDAiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDcsMSkiLz4KPC9zdmc+Cg==" valign="middle"></a> Deterministic AI Prompt Compiler** <br><span style="font-size: 12px;">Achieves unprecedented AI success rates through zero-touch context assembly. Automatically gathers files, dependencies, and project structure—eliminating manual prompt engineering and copy-paste workflows entirely.</span>  |
|  **<a href="https://github.com/8an3/dev-notes/blob/main/docs/CSS.md"  style="font-size: 12px;"><img src="https://img.shields.io/badge/THOR-0284c7?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij4KPHBhdGggZD0iTTAgMCBDMC42NiAwIDEuMzIgMCAyIDAgQzIuMjA2MjUgMC45MDc1IDIuNDEyNSAxLjgxNSAyLjYyNSAyLjc1IEM0LjMyMDQwNzkgNi43NTczMjc3NiA2LjI3NTQ5Nzg0IDcuODk0ODQ2NjEgMTAgMTAgQzguODkyNDIzNzggMTIuOTE5OTczNjcgOC4yMjE4NjQxNSAxMy44NzU1Mzk2MiA1LjQzNzUgMTUuNDM3NSBDMi43NDU2OTcxNSAxNi43OTA2MjcxMiAyLjc0NTY5NzE1IDE2Ljc5MDYyNzEyIDIuMTg3NSAxOS42ODc1IEMyLjEyNTYyNSAyMC40NTA2MjUgMi4wNjM3NSAyMS4yMTM3NSAyIDIyIEMxLjM0IDIyIDAuNjggMjIgMCAyMiBDMCAxNC43NCAwIDcuNDggMCAwIFogTTIgOCBDMiA5Ljk4IDIgMTEuOTYgMiAxNCBDMy4zMiAxMy4zNCA0LjY0IDEyLjY4IDYgMTIgQzYgMTEuMzQgNiAxMC42OCA2IDEwIEM0LjY4IDkuMzQgMy4zNiA4LjY4IDIgOCBaICIgZmlsbD0iIzAwMDAwMCIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoNywxKSIvPgo8L3N2Zz4K" valign="middle"></a> Tailwind V4 Plug-In** <br><span style="font-size: 12px;">Don't want to upgrade from v3? Me neither, but that's ok... I got you, just plug and play </span> | **<a href="https://github.com/8an3/dev-notes/blob/main/docs/CSS.md" style="font-size: 12px;"><img src="https://img.shields.io/badge/THOR-0284c7?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij4KPHBhdGggZD0iTTAgMCBDMC42NiAwIDEuMzIgMCAyIDAgQzIuMjA2MjUgMC45MDc1IDIuNDEyNSAxLjgxNSAyLjYyNSAyLjc1IEM0LjMyMDQwNzkgNi43NTczMjc3NiA2LjI3NTQ5Nzg0IDcuODk0ODQ2NjEgMTAgMTAgQzguODkyNDIzNzggMTIuOTE5OTczNjcgOC4yMjE4NjQxNSAxMy44NzU1Mzk2MiA1LjQzNzUgMTUuNDM3NSBDMi43NDU2OTcxNSAxNi43OTA2MjcxMiAyLjc0NTY5NzE1IDE2Ljc5MDYyNzEyIDIuMTg3NSAxOS42ODc1IEMyLjEyNTYyNSAyMC40NTA2MjUgMi4wNjM3NSAyMS4yMTM3NSAyIDIyIEMxLjM0IDIyIDAuNjggMjIgMCAyMiBDMCAxNC43NCAwIDcuNDggMCAwIFogTTIgOCBDMiA5Ljk4IDIgMTEuOTYgMiAxNCBDMy4zMiAxMy4zNCA0LjY0IDEyLjY4IDYgMTIgQzYgMTEuMzQgNiAxMC42OCA2IDEwIEM0LjY4IDkuMzQgMy4zNiA4LjY4IDIgOCBaICIgZmlsbD0iIzAwMDAwMCIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoNywxKSIvPgo8L3N2Zz4K" valign="middle"></a> Tailwind Preset Config Ngin**<br><span style="font-size: 12px;">By only modifying 3 variables, you have 525+ combinations in options in terms of not only how your site looks but also feels. Supply a preset, theme and font and whether it be sizing, colors, spacing, padding, typography... All factors change dynamically across your entire project.</span>  |
| **★ Live VS Code Internals Inspector**<br><span style="font-size: 12px;">The only UI-driven tool to expose VS Code's internal context and config APIs. Debug and manipulate workspace state in real-time without writing a single line of code.</span>  | **<a href="https://github.com/8an3/dev-notes/blob/main/docs/RÚNAR.md" style="font-size: 12px;"><img src="https://img.shields.io/badge/RÚNAR%20-0284c7?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBzdGFuZGFsb25lPSJubyI/Pgo8IURPQ1RZUEUgc3ZnIFBVQkxJQyAiLS8vVzNDLy9EVEQgU1ZHIDIwMDEwOTA0Ly9FTiIKICJodHRwOi8vd3d3LnczLm9yZy9UUi8yMDAxL1JFQy1TVkctMjAwMTA5MDQvRFREL3N2ZzEwLmR0ZCI+CjxzdmcgdmVyc2lvbj0iMS4wIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciCiB3aWR0aD0iMjQuMDAwMDAwcHQiIGhlaWdodD0iMjQuMDAwMDAwcHQiIHZpZXdCb3g9IjAgMCAyNC4wMDAwMDAgMjQuMDAwMDAwIgogcHJlc2VydmVBc3BlY3RSYXRpbz0ieE1pZFlNaWQgbWVldCI+CjxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAuMDAwMDAwLDI0LjAwMDAwMCkgc2NhbGUoMC4xMDAwMDAsLTAuMTAwMDAwKSIKZmlsbD0iIzAwMDAwMCIgc3Ryb2tlPSJub25lIj4KPHBhdGggZD0iTTcwIDEyMCBjMCAtNjAgNCAtMTAwIDEwIC0xMDAgNiAwIDEwIDE3IDEwIDM4IGwwIDM3IDM0IC00MCBjMTkgLTIyCjM3IC0zOCA0MCAtMzUgMyAzIC0xMyAyNiAtMzQgNTIgbC00MCA0NiA0MSAyNyA0MSAyNyAtMzggMjQgYy02MiAzOCAtNjQgMzYKLTY0IC03NnogbTcwIDUwIGMwIC00IC0xMSAtMTIgLTI1IC0xOCAtMjQgLTExIC0yNSAtMTAgLTI1IDE4IDAgMjggMSAyOSAyNQoxOCAxNCAtNiAyNSAtMTQgMjUgLTE4eiIvPgo8cGF0aCBkPSJNMjE5IDE3MyBjLTEzIC0xNiAtMTIgLTE3IDQgLTQgMTYgMTMgMjEgMjEgMTMgMjEgLTIgMCAtMTAgLTggLTE3Ci0xN3oiLz4KPC9nPgo8L3N2Zz4K" valign="middle"></a> Snippet Development Studio**<br><span style="font-size: 12px;">A full-featured web IDE for snippets with Monaco editor integration. Build and share team snippets 10x faster than the native JSON editor.</span>  |
| **<a href="https://github.com/8an3/dev-notes/blob/main/docs/ATLAS.md" style="font-size: 12px;"><img src="https://img.shields.io/badge/ATLAS%20-0284c7?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPCFET0NUWVBFIHN2ZyBQVUJMSUMgIi0vL1czQy8vRFREIFNWRyAxLjEvL0VOIiAiaHR0cDovL3d3dy53My5vcmcvR3JhcGhpY3MvU1ZHLzEuMS9EVEQvc3ZnMTEuZHRkIj4KPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEuMSIgd2lkdGg9IjE5cHgiIGhlaWdodD0iMjRweCIgc3R5bGU9InNoYXBlLXJlbmRlcmluZzpnZW9tZXRyaWNQcmVjaXNpb247IHRleHQtcmVuZGVyaW5nOmdlb21ldHJpY1ByZWNpc2lvbjsgaW1hZ2UtcmVuZGVyaW5nOm9wdGltaXplUXVhbGl0eTsgZmlsbC1ydWxlOmV2ZW5vZGQ7IGNsaXAtcnVsZTpldmVub2RkIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayI+CjxnPjxwYXRoIHN0eWxlPSJvcGFjaXR5OjAuNjAxIiBmaWxsPSIjMDAwMDAwIiBkPSJNIDguNSwyLjUgQyAxMS42MjMxLDcuMzIyMTYgMTQuMjg5NywxMi40ODg4IDE2LjUsMThDIDE1Ljk3NDcsMTguNjkyNCAxNS4zMDgxLDE5LjE5MjQgMTQuNSwxOS41QyAxMS4zMDA5LDEzLjQ5NTYgNy42MzQyNiwxMy40OTU2IDMuNSwxOS41QyAyLjUsMTkuMTY2NyAxLjgzMzMzLDE4LjUgMS41LDE3LjVDIDQuMTIwNzIsMTIuNTk0MSA2LjQ1NDA1LDcuNTk0MDkgOC41LDIuNSBaIE0gOC41LDguNSBDIDEwLjczODgsMTAuMDAxMiAxMC43Mzg4LDExLjMzNDUgOC41LDEyLjVDIDcuNzA4NCwxMS4zMDAyIDcuNzA4NCw5Ljk2NjkgOC41LDguNSBaIi8+PC9nPgo8L3N2Zz4K" valign="middle"></a> Workspace Layouts**<br><span style="font-size: 12px;">Total environment restoration in one click. Instantly reset your theme, UI visibility, terminals, tabs, and view focus for a perfect setup every time.</span>  | **<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md" style="font-size: 12px;"><img src="https://img.shields.io/badge/BIFRÖST%20-0284c7?style=plastic&logo=data:image/png;base64,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" valign="middle"></a> Command Palette on Steroids**<br><span style="font-size: 12px;">Access a library of 5,175+ searchable commands with deep descriptions and instant category filtering. </span> |
| **<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md" style="font-size: 12px;"><img src="https://img.shields.io/badge/BIFRÖST%20-0284c7?style=plastic&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAsAAAAYCAYAAAAs7gcTAAABamVYSWZJSSoACAAAAAsAAAEEAAEAAAALAAAAAQEEAAEAAAAYAAAAAgEDAAMAAACSAAAAEgEDAAEAAAABAAAAGgEFAAEAAACYAAAAGwEFAAEAAACgAAAAKAEDAAEAAAADAAAAMQECAAsAAACoAAAAMgECABQAAAC0AAAAaYcEAAEAAADcAAAAA5ACABQAAADIAAAAAAAAAAgACAAIAPwpAABbAAAA/CkAAFsAAABHSU1QIDMuMC42AAAyMDI2OjAxOjE3IDAwOjQ1OjMzADIwMjY6MDE6MTYgMjM6NDE6MDgABgADkAIAFAAAACoBAAAEkAIAFAAAAD4BAAAQkAIABwAAAFIBAAARkAIABwAAAFoBAAASkAIABwAAAGIBAAABoAMAAQAAAAEAAAAAAAAAMjAyNjowMToxNiAyMzo0MTowOAAyMDI2OjAxOjE2IDIzOjQxOjA4AC0wNTowMAAALTA1OjAwAAAtMDU6MDAAAJV/SgAAAAGFaUNDUElDQyBwcm9maWxlAAB4nH2RvUvDUBTFT1OlIhURO4g4ZGid7KIijqUVi2ChtBVadTB56Rc0aUhSXBwF14KDH4tVBxdnXR1cBUHwA8Q/QJwUXaTE+5JCixgvPPLjvHtO3rsPEFo1ppp9MUDVLCOTjIv5wqoYeIUPIwDmEJGYqaeyizl41tc9dVPdRXmWd9+fNaQUTQb4ROIY0w2LeIP/edPSOe8Th1hFUojPiacMOiDxI9dll984lx0WeGbIyGUSxCFisdzDcg+ziqESzxKHFVWjfCHvssJ5i7Naa7DOOfkNg0VtJct1WhNIYgkppCFCRgNV1GAhSl+NFBMZ2o97+Mcdf5pcMrmqYORYQB0qJMcP/ga/Z2uWZqbdpGAc6H+x7Y8IENgF2k3b/j627fYJ4H8GrrSuv94C5j9Jb3a18BEwvA1cXHc1eQ+43AHGnnTJkBzJT0solYD3M3qmAjB6CwyuuXPr7OP0AcjRrJZvgINDYLJM2ese9x7ondu/PZ35/QDS3XLNzHxdlAAAAAlwSFlzAAAuIwAALiMBeKU/dgAAAAd0SU1FB+oBEQUtJLQs99sAAARDSURBVDgRATgEx/sDAAAAAQAAABUAAAAJAAAA+gAAAP8AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADwAAANYAAADnAAAAggAAABIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADgAAAN0AAADlAAAA9AAAAMIAAAA3AAAAAQAAAAAAAAAAAAAAAAAAAAACAAAA/gAAAPkAAAC0AAAAWwAAABQAAAC1AAAAdgAAAAwAAAAAAAAAAAAAAAAAAAAADAAAANYAAACWAAAAAAAAAB0AAACgAAAA9QAAALYAAAAsAAAAAQAAAAAAAAAADAAAANYAAACWAAAAAAAAAAAAAAAHAAAAWgAAAOMAAADlAAAAYgAAAAMAAAAADAAAANYAAACWAAAAAAAAAAAAAAAAAAAAAQAAADsAAADrAAAA6QAAABECAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABAAAANgAAAIsAAAAGAAAAmQAAAPUAAAAADAAAANYAAACWAAAAAAAAAAkAAABrAAAA6wAAANcAAABKAAAAAwAAAAAAAAAADAAAANYAAACWAAAAHgAAAKkAAAD3AAAApgAAACAAAAAAAAAAAAAAAAAAAAAADAAAANYAAADIAAAA1gAAAOoAAABrAAAACAAAAAAAAAAAAAAAAAAAAAAAAAAADAAAANYAAAD+AAAAyAAAADQAAAACAAAAAAAAAAAAAAAAAAAAAAAAAAACAAAAAAAAAAAAAAAAAAAA3AAAAOIAAAD+AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADAAAANYAAADdAAAA7gAAAMwAAAA+AAAAAQAAAAAAAAAAAAAAAAAAAAACAAAAAAAAAAAAAAC6AAAAVQAAAAUAAACxAAAAcgAAAAsAAAAAAAAAAAAAAAAAAAAADAAAANYAAACWAAAAAAAAABsAAACfAAAA9gAAALAAAAAkAAAAAAAAAAAAAAAADAAAANYAAACWAAAAAAAAAAAAAAAHAAAAYgAAAOgAAADbAAAAUgAAAAIAAAAADAAAANYAAACWAAAAAAAAAAAAAAAAAAAAAQAAAEAAAADsAAAA5gAAABACAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACAAAALgAAAIAAAAAIAAAAsAAAAPcAAAAADAAAANYAAACWAAAAAAAAAAoAAABtAAAA6QAAANwAAABVAAAABQAAAAAAAAAADAAAANYAAACWAAAAJwAAAK0AAAD4AAAApgAAACQAAAAAAAAAAAAAAAAAAAAADQAAANoAAADOAAAA4AAAAOQAAABlAAAACAAAAAAAAAAAAAAAAAAAAAAAAAAADwAAAOQAAAD7AAAAtgAAACoAAAABAAAAAAAAAAAAAAAAAAAAAAAAAAABAAAABAAAAD4AAAD+AAAAzAAAAPQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAxvVG/2SZj4wAAAABJRU5ErkJggg==" valign="middle"></a> Intelligent Command Ngin**<br><span style="font-size: 12px;">Master 17 execution patterns including sequential, concurrent, and mixed-mode grouping. Run PowerShell and WSL Bash side-by-side in unified, color-coded terminals.</span>  | <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#L55">**☆ Visual Command Architecture**</a><br><span style="font-size: 12px;">A powerful tree view featuring 520+ icons and unlimited nesting. Find and execute complex workflows faster than the standard palette.</span> |
| <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md">**☆ Enterprise Config Scaling**</a><br><span style="font-size: 12px;">Built for complexity. Battle-tested across 45+ workspaces managing 20,000+ lines of configuration with seamless Global-to-Workspace merging.</span> | <a href="https://github.com/8an3/dev-notes/blob/main/docs/STATUS_BAR_MENUS.md">**★ Enterprise-Grade Bookmarks**</a><br><span style="font-size: 12px;">Global, shareable, and line-specific bookmarks with unlimited nested organization and integrated search.</span> |
| <a href="https://github.com/8an3/dev-notes/blob/main/docs/MUNINN.md#L84">**★ Auto-Generated Prisma Schemas**</a><br><span style="font-size: 12px;">Eliminate manual maintenance. The engine scans your codebase and automatically generates or updates your Prisma schemas on the fly.</span> | <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#L145">**☆ Extension Dev Automation**</a><br><span style="font-size: 12px;">Skip the CI/CD overhead. One-click local packaging and installation lets you test and ship extensions in seconds.</span> |
| <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#L787">**☆ Context-Aware Settings Toggles**</a><br><span style="font-size: 12px;">Dynamically generated UI toggles for every VS Code setting. Manage your entire environment and all installed extensions with one-click simplicity.</span> | <a href="https://github.com/8an3/dev-notes/blob/main/docs/STATUS_BAR_MENUS.md">**★ Professional Clipboard History**</a><br>A high-performance 100-item history with hover previews. Pro-level clipboard management built directly into your editor. |
| <a href="https://catalyst-software.vercel.app/Catalyst/UI/home/list">**☆ Catalyst-UI: X**</a><br> | **<a href="https://github.com/8an3/dev-notes/blob/main/docs/ODIN.md#odin" style="font-size: 12px;"><img src="https://img.shields.io/badge/ODIN-0284c7?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij4KPHBhdGggZD0iTTAgMCBDNy4xNzM5MTMwNCAyLjM5MTMwNDM1IDcuMTczOTEzMDQgMi4zOTEzMDQzNSAxMCA1IEMxMCA1LjY2IDEwIDYuMzIgMTAgNyBDNS4yNSA2LjEyNSA1LjI1IDYuMTI1IDMgNSBDMyA1Ljk5IDMgNi45OCAzIDggQzYuNDY1IDkuOTggNi40NjUgOS45OCAxMCAxMiBDMTAgMTIuOTkgMTAgMTMuOTggMTAgMTUgQzUuMjUgMTMuMTI1IDUuMjUgMTMuMTI1IDMgMTIgQzIuNjcgMTUuMyAyLjM0IDE4LjYgMiAyMiBDMS4zNCAyMiAwLjY4IDIyIDAgMjIgQzAgMTQuNzQgMCA3LjQ4IDAgMCBaICIgZmlsbD0iIzAwMDAwMCIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoNywxKSIvPgo8L3N2Zz4K" valign="middle"></a> Search Editor**<br><span style="font-size: 12px;">S Code's search editor reimagined with live find/replace across all results. Edit matches directly in the search view and save changes to all files at once—no navigation required.</span> |
| | <a href="https://github.com/8an3/dev-notes/blob/main/docs/LAYOUT.md">**★ Ultimate Settings.json Guide**</a><br><span style="font-size: 12px;">The definitive deep-dive into VS Code's hidden configuration APIs and theme customization. Reveals undocumented settings, solves critical performance bottlenecks, and explains the architecture behind this extension's unique capabilities.</span> |

<hr />

<p align="center">
  <b>100+ Dev Tools. One Extension. Zero Bloat.</b><br>
  <span>Outperforms 15+ standalone extensions combined. Auto-switches between 45+ workspaces. Proven at 20,000+ settings.</span><br>
  <b>The only extension designed to scale with you over time.</b>
</p>

<div align="center">

<br><br>






## Popular Features

<a href="https://github.com/8an3/dev-notes/blob/main/docs/LAYOUT.md">![Atlas: Workspace Layouts](https://img.shields.io/badge/-ATLAS:%20Workspace%20Layouts-10B981?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPCFET0NUWVBFIHN2ZyBQVUJMSUMgIi0vL1czQy8vRFREIFNWRyAxLjEvL0VOIiAiaHR0cDovL3d3dy53My5vcmcvR3JhcGhpY3MvU1ZHLzEuMS9EVEQvc3ZnMTEuZHRkIj4KPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEuMSIgd2lkdGg9IjE5cHgiIGhlaWdodD0iMjRweCIgc3R5bGU9InNoYXBlLXJlbmRlcmluZzpnZW9tZXRyaWNQcmVjaXNpb247IHRleHQtcmVuZGVyaW5nOmdlb21ldHJpY1ByZWNpc2lvbjsgaW1hZ2UtcmVuZGVyaW5nOm9wdGltaXplUXVhbGl0eTsgZmlsbC1ydWxlOmV2ZW5vZGQ7IGNsaXAtcnVsZTpldmVub2RkIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayI+CjxnPjxwYXRoIHN0eWxlPSJvcGFjaXR5OjAuNjAxIiBmaWxsPSIjMDAwMDAwIiBkPSJNIDguNSwyLjUgQyAxMS42MjMxLDcuMzIyMTYgMTQuMjg5NywxMi40ODg4IDE2LjUsMThDIDE1Ljk3NDcsMTguNjkyNCAxNS4zMDgxLDE5LjE5MjQgMTQuNSwxOS41QyAxMS4zMDA5LDEzLjQ5NTYgNy42MzQyNiwxMy40OTU2IDMuNSwxOS41QyAyLjUsMTkuMTY2NyAxLjgzMzMzLDE4LjUgMS41LDE3LjVDIDQuMTIwNzIsMTIuNTk0MSA2LjQ1NDA1LDcuNTk0MDkgOC41LDIuNSBaIE0gOC41LDguNSBDIDEwLjczODgsMTAuMDAxMiAxMC43Mzg4LDExLjMzNDUgOC41LDEyLjVDIDcuNzA4NCwxMS4zMDAyIDcuNzA4NCw5Ljk2NjkgOC41LDguNSBaIi8+PC9nPgo8L3N2Zz4K&logoColor=fff)</a> 
<a href="https://catalyst-software.vercel.app/Catalyst/Prompt">![Apollo: Deterministic AI Prompt Compiler](https://img.shields.io/badge/-LOKI:%20Deterministic%20Prompt%20Compiler-8B5CF6?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij4KPHBhdGggZD0iTTAgMCBDNC43ODA4OTg4NCAxLjkxMjM1OTU0IDYuNzA3MzQ3NiAzLjIzNjk2ODY5IDEwIDcgQzEwIDcuNjYgMTAgOC4zMiAxMCA5IEM3LjA4NDgyNzA4IDcuOTI1OTg4OTIgNS4yMjE4OTgyNCA3LjIyMTg5ODI0IDMgNSBDMi42NyAxMC42MSAyLjM0IDE2LjIyIDIgMjIgQzEuMzQgMjIgMC42OCAyMiAwIDIyIEMwIDE0Ljc0IDAgNy40OCAwIDAgWiAiIGZpbGw9IiMwMDAwMDAiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDcsMSkiLz4KPC9zdmc+Cg==&logoColor=fff)</a> 
<a href="https://github.com/8an3/dev-notes/blob/main/docs/RÚNAR.md">![RÚNAR: Snippet Studio](https://img.shields.io/badge/-RÚNAR:%20Snippet%20Studio-EC4899?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBzdGFuZGFsb25lPSJubyI/Pgo8IURPQ1RZUEUgc3ZnIFBVQkxJQyAiLS8vVzNDLy9EVEQgU1ZHIDIwMDEwOTA0Ly9FTiIKICJodHRwOi8vd3d3LnczLm9yZy9UUi8yMDAxL1JFQy1TVkctMjAwMTA5MDQvRFREL3N2ZzEwLmR0ZCI+CjxzdmcgdmVyc2lvbj0iMS4wIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciCiB3aWR0aD0iMjQuMDAwMDAwcHQiIGhlaWdodD0iMjQuMDAwMDAwcHQiIHZpZXdCb3g9IjAgMCAyNC4wMDAwMDAgMjQuMDAwMDAwIgogcHJlc2VydmVBc3BlY3RSYXRpbz0ieE1pZFlNaWQgbWVldCI+CjxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAuMDAwMDAwLDI0LjAwMDAwMCkgc2NhbGUoMC4xMDAwMDAsLTAuMTAwMDAwKSIKZmlsbD0iIzAwMDAwMCIgc3Ryb2tlPSJub25lIj4KPHBhdGggZD0iTTcwIDEyMCBjMCAtNjAgNCAtMTAwIDEwIC0xMDAgNiAwIDEwIDE3IDEwIDM4IGwwIDM3IDM0IC00MCBjMTkgLTIyCjM3IC0zOCA0MCAtMzUgMyAzIC0xMyAyNiAtMzQgNTIgbC00MCA0NiA0MSAyNyA0MSAyNyAtMzggMjQgYy02MiAzOCAtNjQgMzYKLTY0IC03NnogbTcwIDUwIGMwIC00IC0xMSAtMTIgLTI1IC0xOCAtMjQgLTExIC0yNSAtMTAgLTI1IDE4IDAgMjggMSAyOSAyNQoxOCAxNCAtNiAyNSAtMTQgMjUgLTE4eiIvPgo8cGF0aCBkPSJNMjE5IDE3MyBjLTEzIC0xNiAtMTIgLTE3IDQgLTQgMTYgMTMgMjEgMjEgMTMgMjEgLTIgMCAtMTAgLTggLTE3Ci0xN3oiLz4KPC9nPgo8L3N2Zz4K&logoColor=fff)</a> 
<a href="https://github.com/8an3/dev-notes/blob/main/docs/CATALYST-UI.md">![Catalyst-UI: X](https://img.shields.io/badge/-Catalyst--UI:%20X-3B82F6?style=plastic&logo=react&logoColor=fff)</a> 
<a href="https://www.npmjs.com/package/@catalystsoftware/icons">![Catalyst Icons](https://img.shields.io/badge/-Catalyst%20Icons-6366F1?style=plastic&logo=iconify&logoColor=fff)</a> 

## New Features

<a href="https://github.com/8an3/dev-notes/blob/main/docs/THOR.md#L251">![THOR: Tailwind V4 Plugin](https://img.shields.io/badge/-THOR:%20Tailwind%20V4%20Plugin-06B6D4?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij4KPHBhdGggZD0iTTAgMCBDMC42NiAwIDEuMzIgMCAyIDAgQzIuMjA2MjUgMC45MDc1IDIuNDEyNSAxLjgxNSAyLjYyNSAyLjc1IEM0LjMyMDQwNzkgNi43NTczMjc3NiA2LjI3NTQ5Nzg0IDcuODk0ODQ2NjEgMTAgMTAgQzguODkyNDIzNzggMTIuOTE5OTczNjcgOC4yMjE4NjQxNSAxMy44NzU1Mzk2MiA1LjQzNzUgMTUuNDM3NSBDMi43NDU2OTcxNSAxNi43OTA2MjcxMiAyLjc0NTY5NzE1IDE2Ljc5MDYyNzEyIDIuMTg3NSAxOS42ODc1IEMyLjEyNTYyNSAyMC40NTA2MjUgMi4wNjM3NSAyMS4yMTM3NSAyIDIyIEMxLjM0IDIyIDAuNjggMjIgMCAyMiBDMCAxNC43NCAwIDcuNDggMCAwIFogTTIgOCBDMiA5Ljk4IDIgMTEuOTYgMiAxNCBDMy4zMiAxMy4zNCA0LjY0IDEyLjY4IDYgMTIgQzYgMTEuMzQgNiAxMC42OCA2IDEwIEM0LjY4IDkuMzQgMy4zNiA4LjY4IDIgOCBaICIgZmlsbD0iIzAwMDAwMCIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoNywxKSIvPgo8L3N2Zz4K&logoColor=fff)</a>
<a href="https://github.com/8an3/dev-notes/blob/main/docs/THOR.md">![THOR: tailwind.config Preset Engine](https://img.shields.io/badge/-THOR:%20tailwind.config%20Preset%20Engine-0EA5E9?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij4KPHBhdGggZD0iTTAgMCBDMC42NiAwIDEuMzIgMCAyIDAgQzIuMjA2MjUgMC45MDc1IDIuNDEyNSAxLjgxNSAyLjYyNSAyLjc1IEM0LjMyMDQwNzkgNi43NTczMjc3NiA2LjI3NTQ5Nzg0IDcuODk0ODQ2NjEgMTAgMTAgQzguODkyNDIzNzggMTIuOTE5OTczNjcgOC4yMjE4NjQxNSAxMy44NzU1Mzk2MiA1LjQzNzUgMTUuNDM3NSBDMi43NDU2OTcxNSAxNi43OTA2MjcxMiAyLjc0NTY5NzE1IDE2Ljc5MDYyNzEyIDIuMTg3NSAxOS42ODc1IEMyLjEyNTYyNSAyMC40NTA2MjUgMi4wNjM3NSAyMS4yMTM3NSAyIDIyIEMxLjM0IDIyIDAuNjggMjIgMCAyMiBDMCAxNC43NCAwIDcuNDggMCAwIFogTTIgOCBDMiA5Ljk4IDIgMTEuOTYgMiAxNCBDMy4zMiAxMy4zNCA0LjY0IDEyLjY4IDYgMTIgQzYgMTEuMzQgNiAxMC42OCA2IDEwIEM0LjY4IDkuMzQgMy4zNiA4LjY4IDIgOCBaICIgZmlsbD0iIzAwMDAwMCIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoNywxKSIvPgo8L3N2Zz4K&logoColor=fff)</a> 
<a href="https://github.com/8an3/dev-notes/blob/main/docs/ODIN.md">![ODIN: Search Editor](https://img.shields.io/badge/-ODIN:%20Search%20Editor-F59E0B?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij4KPHBhdGggZD0iTTAgMCBDNy4xNzM5MTMwNCAyLjM5MTMwNDM1IDcuMTczOTEzMDQgMi4zOTEzMDQzNSAxMCA1IEMxMCA1LjY2IDEwIDYuMzIgMTAgNyBDNS4yNSA2LjEyNSA1LjI1IDYuMTI1IDMgNSBDMyA1Ljk5IDMgNi45OCAzIDggQzYuNDY1IDkuOTggNi40NjUgOS45OCAxMCAxMiBDMTAgMTIuOTkgMTAgMTMuOTggMTAgMTUgQzUuMjUgMTMuMTI1IDUuMjUgMTMuMTI1IDMgMTIgQzIuNjcgMTUuMyAyLjM0IDE4LjYgMiAyMiBDMS4zNCAyMiAwLjY4IDIyIDAgMjIgQzAgMTQuNzQgMCA3LjQ4IDAgMCBaICIgZmlsbD0iIzAwMDAwMCIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoNywxKSIvPgo8L3N2Zz4K&logoColor=fff)</a> 

## Upcoming Features

![MÍMIR: Dev Archive](https://img.shields.io/badge/-MÍMIR:%20Dev%20Archive-64748B?style=plastic&logo=archive&logoColor=fff)
![VALHALLA: SQLite Editor / Viewer](https://img.shields.io/badge/-VALHALLA:%20SQLite%20Editor%20/%20Viewer-475569?style=plastic&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAgAAAAYCAYAAADH2bwQAAAA4mVYSWZJSSoACAAAAAoAAAEEAAEAAAAIAAAAAQEEAAEAAAAYAAAAAgEDAAMAAACGAAAAEgEDAAEAAAABAAAAGgEFAAEAAACMAAAAGwEFAAEAAACUAAAAKAEDAAEAAAACAAAAMQECAAsAAACcAAAAMgECABQAAACoAAAAaYcEAAEAAAC8AAAAAAAAAAgACAAIACwBAAABAAAALAEAAAEAAABHSU1QIDMuMC42AAAyMDI2OjAxOjE3IDA2OjQ1OjM5AAIAEJACAAcAAADaAAAAAaADAAEAAAABAAAAAAAAAC0wNTowMAAAX9fYBQAAAYVpQ0NQSUNDIHByb2ZpbGUAAHicfZG9S8NQFMVPU0XRiohFRBwyVCe7VBHHUsUiWChthVYdTF76BU0akhQXR8G14ODHYtXBxVlXB1dBEPwA8Q8QJ0UXKfG+pNAixguP9+O8ew7v3QcIjQpTza4ooGqWkYrHxGxuVex5hQ9D6McIIhIz9UR6MQPP+rqnbqq7MM/y7vuzBpS8yQCfSBxlumERbxDPblo6533iICtJCvE58ZRBFyR+5Lrs8hvnosMCzwwamdQ8cZBYLHaw3MGsZKjEM8QhRdUoX8i6rHDe4qxWaqx1T/7CQF5bSXOd1jjiWEICSYiQUUMZFVgI066RYiJF5zEP/5jjT5JLJlcZjBwLqEKF5PjB/+D3bM3CdMRNCsSA7hfb/pgAenaBZt22v49tu3kC+J+BK63trzaAuU/S620tdAQMbgMX121N3gMud4DRJ10yJEfy0xIKBeD9jL4pBwzfAn1r7txa5zh9ADI0q+Ub4OAQmCxS9rrHu3s75/ZvT2t+P77hcsVEHzaAAAAACXBIWXMAAC4jAAAuIwF4pT92AAAAB3RJTUUH6gERCy0pwAOmbAAAAyNJREFUKBUBGAPn/AAAAAD/AAAA/wAAAJMAAAADAAAAAAAAAAAAAAAAAAAAAAAAAAD/AAAA9wAAAP8AAACwAAAACgAAAAAAAAAAAAAAAAAAAAD/AAAAmgAAAIAAAAD/AAAAygAAABcAAAAAAAAAAAAAAAD/AAAAmQAAAAAAAABlAAAA+wAAAN4AAAAoAAAAAAAAAAD/AAAAmQAAAAAAAAAAAAAAUAAAAPUAAADsAAAAOwAAAAD/AAAAmQAAAAAAAAAAAAAAAAAAAGEAAAD/AAAAtAAAAAD/AAAAmQAAAAAAAAAAAAAAYAAAAPQAAAD1AAAAVgAAAAD/AAAAmQAAAAkAAACZAAAA/wAAANcAAAAtAAAAAAAAAAD/AAAAvQAAANUAAAD/AAAAoAAAAAsAAAAAAAAAAAAAAAD/AAAA/wAAAPQAAABgAAAAAAAAAAAAAAAAAAAAAAAAAAD/AAAA3AAAACoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAD/AAAAmQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAANYOKaFEGdfWAAAAAElFTkSuQmCC&logoColor=fff)
<a href="https://github.com/8an3/dev-notes/blob/main/docs/ATLAS.md">![ATLAS: Workspace Layouts V2](https://img.shields.io/badge/-ATLAS:%20Workspace%20Layouts%20V2-059669?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPCFET0NUWVBFIHN2ZyBQVUJMSUMgIi0vL1czQy8vRFREIFNWRyAxLjEvL0VOIiAiaHR0cDovL3d3dy53My5vcmcvR3JhcGhpY3MvU1ZHLzEuMS9EVEQvc3ZnMTEuZHRkIj4KPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEuMSIgd2lkdGg9IjE5cHgiIGhlaWdodD0iMjRweCIgc3R5bGU9InNoYXBlLXJlbmRlcmluZzpnZW9tZXRyaWNQcmVjaXNpb247IHRleHQtcmVuZGVyaW5nOmdlb21ldHJpY1ByZWNpc2lvbjsgaW1hZ2UtcmVuZGVyaW5nOm9wdGltaXplUXVhbGl0eTsgZmlsbC1ydWxlOmV2ZW5vZGQ7IGNsaXAtcnVsZTpldmVub2RkIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayI+CjxnPjxwYXRoIHN0eWxlPSJvcGFjaXR5OjAuNjAxIiBmaWxsPSIjMDAwMDAwIiBkPSJNIDguNSwyLjUgQyAxMS42MjMxLDcuMzIyMTYgMTQuMjg5NywxMi40ODg4IDE2LjUsMThDIDE1Ljk3NDcsMTguNjkyNCAxNS4zMDgxLDE5LjE5MjQgMTQuNSwxOS41QyAxMS4zMDA5LDEzLjQ5NTYgNy42MzQyNiwxMy40OTU2IDMuNSwxOS41QyAyLjUsMTkuMTY2NyAxLjgzMzMzLDE4LjUgMS41LDE3LjVDIDQuMTIwNzIsMTIuNTk0MSA2LjQ1NDA1LDcuNTk0MDkgOC41LDIuNSBaIE0gOC41LDguNSBDIDEwLjczODgsMTAuMDAxMiAxMC43Mzg4LDExLjMzNDUgOC41LDEyLjVDIDcuNzA4NCwxMS4zMDAyIDcuNzA4NCw5Ljk2NjkgOC41LDguNSBaIi8+PC9nPgo8L3N2Zz4K&logoColor=fff)</a> 
![Log-to-Lens](https://img.shields.io/badge/-TYR:%20Log%20to%20Lens-6B7280?style=plastic&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIxNiIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDE2IDI0IiB2ZXJzaW9uPSIxLjEiPjxwYXRoIGQ9IiIgc3Ryb2tlPSJub25lIiBmaWxsPSIjMDgwNDA0IiBmaWxsLXJ1bGU9ImV2ZW5vZGQiLz48cGF0aCBkPSJNIDMuMjUzIDIuMjUwIEMgLTEuNzIzIDUuNzI5LCAtMC41MzUgNy43MDcsIDQuNTM1IDQuMzg1IEwgNyAyLjc3MCA3IDEzLjM4NSBDIDcgMTkuNzk1LCA3LjM5NiAyNCwgOCAyNCBDIDguNjAzIDI0LCA5IDE5LjgzMywgOSAxMy41MDAgQyA5IDcuNzI1LCA5LjMwMiAzLCA5LjY3MSAzIEMgMTAuMDQwIDMsIDExLjE0OSAzLjczMCwgMTIuMTM0IDQuNjIxIEMgMTMuOTg1IDYuMjk2LCAxNyA1Ljg5NCwgMTcgMy45NzIgQyAxNyAzLjM3MywgMTYuNjAzIDMuMTI3LCAxNi4xMTggMy40MjcgQyAxNS42MzIgMy43MjcsIDE0LjA5OSAzLjA3OSwgMTIuNzEwIDEuOTg2IEMgOS40NDQgLTAuNTgzLCA3LjIxNiAtMC41MjAsIDMuMjUzIDIuMjUwIE0gLTAgNSBDIC0wIDUuNzMzLCAwLjMwMCA2LjAzMywgMC42NjcgNS42NjcgQyAxLjAzMyA1LjMwMCwgMS4wMzMgNC43MDAsIDAuNjY3IDQuMzMzIEMgMC4zMDAgMy45NjcsIC0wIDQuMjY3LCAtMCA1IiBzdHJva2U9Im5vbmUiIGZpbGw9IiMwNDA0MDQiIGZpbGwtcnVsZT0iZXZlbm9kZCIvPjwvc3ZnPg==&logoColor=fff)
![Proxy / Tunnel](https://img.shields.io/badge/-NEMESIS:%20Proxy%20/%20Tunnel-71717A?style=plastic&logo=ngrok&logoColor=fff)
![API Secret Grabber](https://img.shields.io/badge/-HERMES:%20API%20Secret%20Grabber-52525B?style=plastic&logo=1password&logoColor=fff)
![Loki AI](https://img.shields.io/badge/-LOKI:%20Limitless%20AI-A855F7?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij4KPHBhdGggZD0iTTAgMCBDNC43ODA4OTg4NCAxLjkxMjM1OTU0IDYuNzA3MzQ3NiAzLjIzNjk2ODY5IDEwIDcgQzEwIDcuNjYgMTAgOC4zMiAxMCA5IEM3LjA4NDgyNzA4IDcuOTI1OTg4OTIgNS4yMjE4OTgyNCA3LjIyMTg5ODI0IDMgNSBDMi42NyAxMC42MSAyLjM0IDE2LjIyIDIgMjIgQzEuMzQgMjIgMC42OCAyMiAwIDIyIEMwIDE0Ljc0IDAgNy40OCAwIDAgWiAiIGZpbGw9IiMwMDAwMDAiIHRyYW5zZm9ybT0idHJhbnNsYXRlKDcsMSkiLz4KPC9zdmc+Cg==&logoColor=fff)

</div>

<!-- #endregion -->

<!-- #region TOC -->
# The DevStack Pantheon
<pre style="max-width: 800px; white-space: pre-wrap; overflow-wrap: break-word; background-color: transparent;">
/DEVSTACK SYSTEM ROOT/  
├── 📂 TABLE OF CONTENTS/
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/OVERVIEW.md">OVERVIEW</a> 
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/USAGE.md">GETTING STARTED & USAGE</a> 
│   ├── <a href="#license">LICENSE</a> 
│   └── <a href="#acknowledgments">ACKNOWLEDGMENTS</a>
│
├── <img src="https://img.shields.io/badge/❕%20NOTE%20-6b21a8?style=plastic" valign="middle"><span style="font-size: 12px;"> ............................... Badge legend </span>
│   ├── <a href="#category"><img src="https://img.shields.io/badge/📂%20Category%20-475569?style=plastic" valign="middle"></a><span style="font-size: 12px;"> ........................ umbrella for a feature set</span>
│   ├── <a href="#works"><img src="https://img.shields.io/badge/📄%20Feature%20-0284c7?style=plastic" valign="middle"></a><span style="font-size: 12px;"> ......................... Completed and tested</span>
│   ├── <a href="#works-no-docs"><img src="https://img.shields.io/badge/✓%20Works%20(No%20Docs)-059669?style=plastic" valign="middle"></a><span style="font-size: 12px;"> ................. Passed tests, but currently no docs </span>
│   ├── <a href="#untested"><img src="https://img.shields.io/badge/✗%20Untested-EF4444?style=plastic" valign="middle"></a><span style="font-size: 12px;"> ........................ No docs, not tested  </span>
│   ├── <a href="#implemented"><img src="https://img.shields.io/badge/♣%20Implemented-3B82F6?style=plastic" valign="middle"></a><span style="font-size: 12px;"> .................... Implemented, not tested, no docs  </span>
│   ├── <a href="#in-development"><img src="https://img.shields.io/badge/♠%20In%20Development-86198f?style=plastic" valign="middle"></a><span style="font-size: 12px;"> .................. In development  </span>
│   ├── <a href="#planned"><img src="https://img.shields.io/badge/♦%20Planned-ca8a04?style=plastic" valign="middle"></a><span style="font-size: 12px;"> .......................... Feature has been decided upon  </span>
│   ├── <a href="#maybe"><img src="https://img.shields.io/badge/♥%20Maybe-F97316?style=plastic" valign="middle"></a><span style="font-size: 12px;"> .......................... Thinking about it adding it, on the fence  </span>
│   └── <a href="#down"><img src="https://img.shields.io/badge/↓%20Currently%20Down-DC2626?style=plastic" valign="middle"></a><span style="font-size: 12px;"> ................... Feature is currently down</span>
│ 
├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md"><img src="https://img.shields.io/badge/BIFRÖST%20/%20-0284c7?style=plastic&logo=data:image/png;base64,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" valign="middle"></a><span style="font-size: 12px;"> .......................... Terminal and Multi Kernel Ngin</span>
│   ├── 📂 <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#item-types">Item Types</a><span style="font-size: 12px;"> ..................... VFS item types</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#file">`file`</a> <span style="font-size: 12px;">..................... Providing shortcuts to any file in any location </span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#md">`md`</a> <span style="font-size: 12px;">.......................  Same as above, but for md</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#fileatline">`fileAtLine`</a><span style="font-size: 12px;"> ............... Instead opens the file at a specific line number</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#folder">`folder`</a><span style="font-size: 12px;"> ................... To house virtual file items within for organization</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#url">`url`</a><span style="font-size: 12px;"> ...................... When executed, opens that url in your default browser</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#command">`command`</a><span style="font-size: 12px;"> .................. Executes vscode command</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#chain">`chain`</a><span style="font-size: 12px;"> .................... Executes any item type in a sequential firing order</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#concurrent">`concurrent`</a><span style="font-size: 12px;"> ............... Executes all commands, at once</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#cmmdchain">`cmmdChain`</a><span style="font-size: 12px;"> ................ A chain of commands consisting of only vscode commands</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#conditionalchain">`conditionalChain`</a><span style="font-size: 12px;"> ......... Depending on your checks, can execute or not in any form </span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#powershellcommand">`powershellCommand`</a><span style="font-size: 12px;"> ........ Executes powershell commands</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#debiancmd">`debianCMD`</a><span style="font-size: 12px;"> ................ Executes baash commands in WSL's Debian enviroment</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#snippet">`snippet`</a><span style="font-size: 12px;"> .................. Copy snippet body to clipboard</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#copyvalue">`copyValue`</a><span style="font-size: 12px;"> ................ Copy value to clipboard</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#settingstoggle">`settingsToggle`</a><span style="font-size: 12px;"> ........... Toggle workspace or global settings.json key:value pair</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#search">`search`</a><span style="font-size: 12px;"> ................... Searches, executed whenever you need with a click </span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#apicall">`apiCall`</a><span style="font-size: 12px;"> .................. Trigger Pre-made HTTP API requests at any time </span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#tasks">`tasks`</a><span style="font-size: 12px;"> .................... Auto generates within the explorer for easy access</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#npmscripts">`npmScripts`</a><span style="font-size: 12px;"> ............... Same as above but with your packages scripts</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#label">`label`</a><span style="font-size: 12px;"> .................... Visual divider used to break up an area</span>
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#menu"><img src="https://img.shields.io/badge/📄%20menu-3B82F6?style=plastic" valign="middle"></a><span style="font-size: 12px;"> ...................... There are docs but right this second, its untested
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#dependency-manager"><img src="https://img.shields.io/badge/♦%20Dependency%20Manager-ca8a04?style=plastic" valign="middle"></a><span style="font-size: 12px;"> ......... Install/uninstall/update multiple npm packages in one click </span>
│   │   │    ├── <span style="font-size: 12px;">with predefined sets (ie "React setup" installs react, react-dom, types in one go </span>
│   │   │    └── <span style="font-size: 12px;">vs typing each npm install command)</span>
│   │   └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#layout">`layout`</a><span style="font-size: 12px;"> ................... Taking complete control, of vscode and its interface</span>
│   │        ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/ATLAS.md"><img src="https://img.shields.io/badge/ATLAS%20-0284c7?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPCFET0NUWVBFIHN2ZyBQVUJMSUMgIi0vL1czQy8vRFREIFNWRyAxLjEvL0VOIiAiaHR0cDovL3d3dy53My5vcmcvR3JhcGhpY3MvU1ZHLzEuMS9EVEQvc3ZnMTEuZHRkIj4KPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEuMSIgd2lkdGg9IjE5cHgiIGhlaWdodD0iMjRweCIgc3R5bGU9InNoYXBlLXJlbmRlcmluZzpnZW9tZXRyaWNQcmVjaXNpb247IHRleHQtcmVuZGVyaW5nOmdlb21ldHJpY1ByZWNpc2lvbjsgaW1hZ2UtcmVuZGVyaW5nOm9wdGltaXplUXVhbGl0eTsgZmlsbC1ydWxlOmV2ZW5vZGQ7IGNsaXAtcnVsZTpldmVub2RkIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayI+CjxnPjxwYXRoIHN0eWxlPSJvcGFjaXR5OjAuNjAxIiBmaWxsPSIjMDAwMDAwIiBkPSJNIDguNSwyLjUgQyAxMS42MjMxLDcuMzIyMTYgMTQuMjg5NywxMi40ODg4IDE2LjUsMThDIDE1Ljk3NDcsMTguNjkyNCAxNS4zMDgxLDE5LjE5MjQgMTQuNSwxOS41QyAxMS4zMDA5LDEzLjQ5NTYgNy42MzQyNiwxMy40OTU2IDMuNSwxOS41QyAyLjUsMTkuMTY2NyAxLjgzMzMzLDE4LjUgMS41LDE3LjVDIDQuMTIwNzIsMTIuNTk0MSA2LjQ1NDA1LDcuNTk0MDkgOC41LDIuNSBaIE0gOC41LDguNSBDIDEwLjczODgsMTAuMDAxMiAxMC43Mzg4LDExLjMzNDUgOC41LDEyLjVDIDcuNzA4NCwxMS4zMDAyIDcuNzA4NCw5Ljk2NjkgOC41LDguNSBaIi8+PC9nPgo8L3N2Zz4K&logoColor=fff" valign="middle"></a> WS Layout Ngin</a><span style="font-size: 12px;"> . Total environment restoration in one click. Instantly reset </span>
│   │        │   └──  <span style="font-size: 12px;">theme, UI visibility, terminals, tabs, view focus and more</span>
│   │        └── <a href="#in-development"><img src="https://img.shields.io/badge/ATLAS%20V2-86198f?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPCFET0NUWVBFIHN2ZyBQVUJMSUMgIi0vL1czQy8vRFREIFNWRyAxLjEvL0VOIiAiaHR0cDovL3d3dy53My5vcmcvR3JhcGhpY3MvU1ZHLzEuMS9EVEQvc3ZnMTEuZHRkIj4KPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZlcnNpb249IjEuMSIgd2lkdGg9IjE5cHgiIGhlaWdodD0iMjRweCIgc3R5bGU9InNoYXBlLXJlbmRlcmluZzpnZW9tZXRyaWNQcmVjaXNpb247IHRleHQtcmVuZGVyaW5nOmdlb21ldHJpY1ByZWNpc2lvbjsgaW1hZ2UtcmVuZGVyaW5nOm9wdGltaXplUXVhbGl0eTsgZmlsbC1ydWxlOmV2ZW5vZGQ7IGNsaXAtcnVsZTpldmVub2RkIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayI+CjxnPjxwYXRoIHN0eWxlPSJvcGFjaXR5OjAuNjAxIiBmaWxsPSIjMDAwMDAwIiBkPSJNIDguNSwyLjUgQyAxMS42MjMxLDcuMzIyMTYgMTQuMjg5NywxMi40ODg4IDE2LjUsMThDIDE1Ljk3NDcsMTguNjkyNCAxNS4zMDgxLDE5LjE5MjQgMTQuNSwxOS41QyAxMS4zMDA5LDEzLjQ5NTYgNy42MzQyNiwxMy40OTU2IDMuNSwxOS41QyAyLjUsMTkuMTY2NyAxLjgzMzMzLDE4LjUgMS41LDE3LjVDIDQuMTIwNzIsMTIuNTk0MSA2LjQ1NDA1LDcuNTk0MDkgOC41LDIuNSBaIE0gOC41LDguNSBDIDEwLjczODgsMTAuMDAxMiAxMC43Mzg4LDExLjMzNDUgOC41LDEyLjVDIDcuNzA4NCwxMS4zMDAyIDcuNzA4NCw5Ljk2NjkgOC41LDguNSBaIi8+PC9nPgo8L3N2Zz4K&logoColor=fff" valign="middle"></a> <span style="font-size: 12px;">Global, Profile and Workspace context intelligent </span>
│   │            ├── <span style="font-size: 12px;">Stale / garbage data cleaner - VSCode leaves data behind, even after </span>
│   │            │   └── <span style="font-size: 12px;">uninstalling extensions from years ago that you didn't even know was there </span>
│   │            ├── <span style="font-size: 12px;">4 level of user access, varying in levels of complexity starting with:</span>
│   │            │   ├── <span style="font-size: 12px;">Level 1: Muggles ( Basic UI configuration, and UI style manipulation</span>
│   │            │   │    └── <span style="font-size: 12px;">of 18,000 configurations through only 3 choices. Font, preset and theme )</span>
│   │            │   ├── <span style="font-size: 12px;">Level 2: Casual nerds </span>
│   │            │   ├── <span style="font-size: 12px;">Level 3: Power users</span>
│   │            │   ├── <span style="font-size: 12px;">Level 4: SAURON MODE, if you crave a level of manipulation so great that you </span>
│   │            │   │    ├── <span style="font-size: 12px;">just can't satisfy that itch till EVERYTHING is modified exposing, </span>
│   │            │   │    └── <span style="font-size: 12px;">literally, as much as I can get away</span>
│   │            │   ├── <span style="font-size: 12px;">So complicated, microsoft doesnt even attempt trying anymore. Making </span>
│   │            │   ├──<span style="font-size: 12px;"> it so new or experienced, you will not only find it easy</span>
│   │            │   ├── <span style="font-size: 12px;">to use but will find continous use as your skill grows.</span>
│   │            │   ├── <span style="font-size: 12px;">Levels 1-3 will ONLY feature configurations that can be set</span>
│   │            │   ├── <span style="font-size: 12px;">with a toggle or a dropdown menu. So you don't even have </span>
│   │            │   ├── <span style="font-size: 12px;">to look up any documentation. For  the ones who like</span>
│   │            │   ├── <span style="font-size: 12px;">a bit spicier of a experience, sauron mode will host every</span>
│   │            │   ├── <span style="font-size: 12px;">single value that is avialable to manipulate no </span>
│   │            │   ├── <span style="font-size: 12px;">matter how that value gets set. If you think the Ngin</span>
│   │            │   ├── <span style="font-size: 12px;">is crazy in terms of the level of configurations </span>
│   │            │   └── <span style="font-size: 12px;">just wait and see what V2 will have.</span>
│   │            ├── <span style="font-size: 12px;">Ignore all toasts / notifications / recommendations  </span>
│   │            ├── <span style="font-size: 12px;">Custom icons usable through the vscode ui??? Maybe.... </span>
│   │            └── <span style="font-size: 12px;">Workspace context extension toggle ( Another dream has</span>
│   │                 └── <span style="font-size: 12px;">come back from the grave, did NOT see this one coming ) </span>
│   │     
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md">Virtual Filing System</a> .......... Core VFS Engine 
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#files--navigation">Files & Navigation</a> ............. File management and navigation
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#commands--automation">Commands & Automation</a> .......... Command execution and automation workflows
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#terminal-commands">Terminal Commands</a> .............. Terminal command integration
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#utilities">Utilities</a> ...................... Utility functions and helpers
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#project-agnostic-setup">Project Agnostic Setup</a> ......... Framework-agnostic configuration 
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md"><img src="https://img.shields.io/badge/📄%20Move%20VFS%20Item%20-0284c7?style=plastic" valign="middle"></a> .................. Move items with ease with the VSCode ui 
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#copy-workspace-folder"><img src="https://img.shields.io/badge/♦%20Copy%20workspace%20folder-ca8a04?style=plastic" valign="middle"></a> ............. Provides a list of folders contained within other configs, 
│   │    └──  once clicked pastes it into the current configs file
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#auto-generated-items">Auto-Generated Items</a> ........... Automatically generated VFS items
│   │    
│   │    
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md"><img src="https://img.shields.io/badge/♠%20Concurrent-86198f?style=plastic" valign="middle"></a> ........ item type adjustment, migrate from powershell to node for faster, better terminal ux
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md"><img src="https://img.shields.io/badge/♠%20Conditional-86198f?style=plastic" valign="middle"></a> ........ newn item type. conditions:
│   │   ├── always | firstOpen | dailyFirst | custom
│   │   ├── if succesful
│   │   ├── if unsuccesful
│   │   ├── Run command at specific time
│   │   ├── Recurring executions (every hour, daily)
│   │   ├── Cron-like syntax
│   │   ├── Background execution option
│   │   └── Will be created to be best in class, in comparison to other conditional command executions
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md"><img src="https://img.shields.io/badge/VEÐRFÖLNIR-86198f?style=plastic&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAgAAAAYCAYAAADH2bwQAAAA4mVYSWZJSSoACAAAAAoAAAEEAAEAAAAIAAAAAQEEAAEAAAAYAAAAAgEDAAMAAACGAAAAEgEDAAEAAAABAAAAGgEFAAEAAACMAAAAGwEFAAEAAACUAAAAKAEDAAEAAAACAAAAMQECAAsAAACcAAAAMgECABQAAACoAAAAaYcEAAEAAAC8AAAAAAAAAAgACAAIACwBAAABAAAALAEAAAEAAABHSU1QIDMuMC42AAAyMDI2OjAxOjE3IDA2OjQ1OjM5AAIAEJACAAcAAADaAAAAAaADAAEAAAABAAAAAAAAAC0wNTowMAAAX9fYBQAAAYVpQ0NQSUNDIHByb2ZpbGUAAHicfZG9S8NQFMVPU0XRiohFRBwyVCe7VBHHUsUiWChthVYdTF76BU0akhQXR8G14ODHYtXBxVlXB1dBEPwA8Q8QJ0UXKfG+pNAixguP9+O8ew7v3QcIjQpTza4ooGqWkYrHxGxuVex5hQ9D6McIIhIz9UR6MQPP+rqnbqq7MM/y7vuzBpS8yQCfSBxlumERbxDPblo6533iICtJCvE58ZRBFyR+5Lrs8hvnosMCzwwamdQ8cZBYLHaw3MGsZKjEM8QhRdUoX8i6rHDe4qxWaqx1T/7CQF5bSXOd1jjiWEICSYiQUUMZFVgI066RYiJF5zEP/5jjT5JLJlcZjBwLqEKF5PjB/+D3bM3CdMRNCsSA7hfb/pgAenaBZt22v49tu3kC+J+BK63trzaAuU/S620tdAQMbgMX121N3gMud4DRJ10yJEfy0xIKBeD9jL4pBwzfAn1r7txa5zh9ADI0q+Ub4OAQmCxS9rrHu3s75/ZvT2t+P77hcsVEHzaAAAAACXBIWXMAAC4jAAAuIwF4pT92AAAAB3RJTUUH6gERCy0pwAOmbAAAAyNJREFUKBUBGAPn/AAAAAD/AAAA/wAAAJMAAAADAAAAAAAAAAAAAAAAAAAAAAAAAAD/AAAA9wAAAP8AAACwAAAACgAAAAAAAAAAAAAAAAAAAAD/AAAAmgAAAIAAAAD/AAAAygAAABcAAAAAAAAAAAAAAAD/AAAAmQAAAAAAAABlAAAA+wAAAN4AAAAoAAAAAAAAAAD/AAAAmQAAAAAAAAAAAAAAUAAAAPUAAADsAAAAOwAAAAD/AAAAmQAAAAAAAAAAAAAAAAAAAGEAAAD/AAAAtAAAAAD/AAAAmQAAAAAAAAAAAAAAYAAAAPQAAAD1AAAAVgAAAAD/AAAAmQAAAAkAAACZAAAA/wAAANcAAAAtAAAAAAAAAAD/AAAAvQAAANUAAAD/AAAAoAAAAAsAAAAAAAAAAAAAAAD/AAAA/wAAAPQAAABgAAAAAAAAAAAAAAAAAAAAAAAAAAD/AAAA3AAAACoAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAD/AAAAmQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAANYOKaFEGdfWAAAAAElFTkSuQmCC&logoColor=fff" valign="middle"></a> ........ Resource, hardware & process information  
│   │   ├── providing information on resources, ports used, etc, a HWInfo for your vscode, if you will.
│   │   ├── List views of currently running processes, even background ones, provding info on resource usage
│   │   ├── port numbers used, quick kill, quick restart buttons.
│   │   └── Gauges displaying usages for cpu, memory, storage
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md"><img src="https://img.shields.io/badge/GINNUNGAGAP-86198f?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBzdGFuZGFsb25lPSJubyI/Pgo8IURPQ1RZUEUgc3ZnIFBVQkxJQyAiLS8vVzNDLy9EVEQgU1ZHIDIwMDEwOTA0Ly9FTiIKICJodHRwOi8vd3d3LnczLm9yZy9UUi8yMDAxL1JFQy1TVkctMjAwMTA5MDQvRFREL3N2ZzEwLmR0ZCI+CjxzdmcgdmVyc2lvbj0iMS4wIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciCiB3aWR0aD0iMTIuMDAwMDAwcHQiIGhlaWdodD0iMjQuMDAwMDAwcHQiIHZpZXdCb3g9IjAgMCAxMi4wMDAwMDAgMjQuMDAwMDAwIgogcHJlc2VydmVBc3BlY3RSYXRpbz0ieE1pZFlNaWQgbWVldCI+CjxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAuMDAwMDAwLDI0LjAwMDAwMCkgc2NhbGUoMC4xMDAwMDAsLTAuMTAwMDAwKSIKZmlsbD0iIzAwMDAwMCIgc3Ryb2tlPSJub25lIj4KPHBhdGggZD0iTTggMjM1IGMtNCAtNCA0IC0zMCAxOCAtNTggbDI2IC01MCAtMjUgLTU4IGMtMTQgLTMzIC0yMiAtNjEgLTE3Ci02NCA0IC0yIDE3IDE5IDI5IDQ4IGwyMiA1MiAyMSAtNDcgYzExIC0yNyAyNCAtNDggMjkgLTQ4IDkgMCAtMSAzMiAtMjYgODAKLTE0IDI3IC0xMyAzMyA5IDg0IDE0IDMxIDIxIDU4IDE2IDYxIC00IDMgLTE2IC0xNSAtMjYgLTQwIC05IC0yNSAtMTkgLTQ1Ci0yMyAtNDUgLTMgMCAtMTUgMjEgLTI2IDQ2IC0xMSAyNSAtMjMgNDMgLTI3IDM5eiIvPgo8L2c+Cjwvc3ZnPgo=" valign="middle"></a> ........ Architecture Templates, pre-configured platform scaffolding  
│   │   ├── think of it as, incorporating remix-stacks into devstack, but less restrictive all the while
│   │   ├── having more features, making it even more powerful, saving even more time
│   │   ├── auto:
│   │   │   ├── install
│   │   │   ├── git initalize and first push
│   │   │   ├── schafold prisma with seed and schema
│   │   │   ├── set up auth and auth routes
│   │   │   ├── pre-configured tooling (eslint, prettier, tsconfig)
│   │   │   ├── create common files (.gitignore, .env.example, README template)
│   │   │   ├── package libraires and configs into groups, so can be used across several platforms
│   │   │   ├── create / overwrite files, folders taking a template project and making it even more custom
│   │   │   ├── tsconfig.json (your preferred settings)
│   │   │   ├── .eslintrc (your rules)
│   │   │   ├── .prettierrc (your formatting)
│   │   │   ├── jest.config.js (your test setup)
│   │   │   ├── docker-compose.yml (your local stack)
│   │   │   ├── Create .gitignore from template
│   │   │   ├── Set up branches (main, develop)
│   │   │   ├── changelog
│   │   │   ├── .env templates per project type
│   │   │   ├── Common variables already filled
│   │   │   ├── Docker Stack Initialization 
│   │   │   ├── Postgres + pgAdmin
│   │   │   ├── Redis
│   │   │   ├── MongoDB + Mongo Express
│   │   │   ├── Your common service stack
│   │   │   ├── CI/CD Pipeline Templates
│   │   │   ├── API Route Boilerplate
│   │   │   ├── Create CRUD endpoints
│   │   │   ├── Error handling wrapper
│   │   │   ├── select readme.md template to be used
│   │   │   ├── Webpack config for your setup
│   │   │   ├── Vite config
│   │   │   ├── Rollup config
│   │   │   ├── Monorepo Setup
│   │   │   └── and more
│   │   ├── any archetecture, any platform
│   │   ├── as I said earlier, think remix-stacks on steroids and platform agnostic. IMO, that was a great feature 
│   │   ├── of remixs. Honestly, I loved it, and I want to have the same commmunity feel in regards to stacks.
│   │   ├── Even hoping for more of an involvement in sharing "stacks", because lets be real, as great as it was
│   │   ├── it did have it's pit falls, as do all platforms have though, but stacks being up there as far as 
│   │   ├── how great of an idea / quality of a feature, and in terms of a platform sharing concept, it had to be
│   │   ├── the best implementation in terms of a user cloning and starting a stack. Maybe not so much on the 
│   │   ├── creator side, but I'm hoping to make that experience... just as easy. As of right now, writing this 
│   │   ├── down so I dont forget either, in terms of anything above and beyond cloning the original project, 
│   │   ├── it might be a great idea to make it so that each configuration, customizatoin, addition or 
│   │   ├── whatever form you can think of it as. Making it so each one starts as a plugin, for example 
│   │   ├── `Auth: route scaffolding and cookie set up or whatever`, creating it as its own object that can 
│   │   ├── be called into any configuration you want or need. This would make it where, not only would
│   │   ├── the "stack" as a whole be shareable, I do plan on having something similar to remixs 
│   │   ├── github thread although something slightly less restrictive so you can search for categories
│   │   ├── with ease in addition to a search function, but it also makes the plug ins shareable,
│   │   ├── coupled with the fact that it can be used on any platform, I think would be a great 
│   │   └── recipe for community involvement. 
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md"><img src="https://img.shields.io/badge/URÐR-86198f?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBzdGFuZGFsb25lPSJubyI/Pgo8IURPQ1RZUEUgc3ZnIFBVQkxJQyAiLS8vVzNDLy9EVEQgU1ZHIDIwMDEwOTA0Ly9FTiIKICJodHRwOi8vd3d3LnczLm9yZy9UUi8yMDAxL1JFQy1TVkctMjAwMTA5MDQvRFREL3N2ZzEwLmR0ZCI+CjxzdmcgdmVyc2lvbj0iMS4wIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciCiB3aWR0aD0iMTQuMDAwMDAwcHQiIGhlaWdodD0iMjQuMDAwMDAwcHQiIHZpZXdCb3g9IjAgMCAxNC4wMDAwMDAgMjQuMDAwMDAwIgogcHJlc2VydmVBc3BlY3RSYXRpbz0ieE1pZFlNaWQgbWVldCI+CjxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAuMDAwMDAwLDI0LjAwMDAwMCkgc2NhbGUoMC4xMDAwMDAsLTAuMTAwMDAwKSIKZmlsbD0iIzAwMDAwMCIgc3Ryb2tlPSJub25lIj4KPHBhdGggZD0iTTcgMjMzIGMtMTMgLTEyIC04IC0yMzMgNCAtMjMzIDggMCAxMCAyOSA2IDEwMCAtMyA1NSAtMyAxMDAgLTIgMTAwCjIgMCAyNyAtNDUgNTYgLTk5IDI5IC01NSA1NiAtOTggNjAgLTk1IDQgMiAtMjAgNTUgLTUzIDExNyAtNjkgMTI5IC02MyAxMTkKLTcxIDExMHoiLz4KPC9nPgo8L3N2Zz4K" valign="middle"></a> ........ Snapshot Engine will be deleted, and re-made from the ground up 
│   │   ├── UI snapshot, that will work cohesively with atlas
│   │   └── workspace snapshot, taking a snapshot of current file and folder structure and contents
│   │       └── with rollback function
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md"><img src="https://img.shields.io/badge/♠%20Auto-Port%20Ngin-86198f?style=plastic" valign="middle"></a> ........ Provide the entire powershell command replacing the port number with ${PORT}  
│   │   ├── so wheenver you have a project that takes up a lot of running servies on ports, instead of assigning
│   │   ├── with possible collission, it auto assigned ports, and auto creates new terminals to run them in,
│   │   └── unless args.concurrent: true
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md"><img src="https://img.shields.io/badge/♠%20Changelog%20Ngin-86198f?style=plastic" valign="middle"></a> ........ Parse commits since last release
│   │   ├── Generate changelog markdown
│   │   ├── Group by type (feat/fix/breaking)
│   │   └── Update version numbers
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md"><img src="https://img.shields.io/badge/♠%20Faker%20Ngin-86198f?style=plastic" valign="middle"></a> ........ Grabs your workspaces schema file and automatically creates a file that generates
│   │   ├──  data for all schema declarations that can be called in your seed file
│   │   ├── Ensures that the automated mock data generation stays seperate from your projects code 
│   │   └──  instead of implementing it into it

│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md"><img src="https://img.shields.io/badge/♠%20Arftifact%20Cache%20Mgr-86198f?style=plastic" valign="middle"></a> ........ Instead of having to open marketplace, or the ms site along with the fact  
│   │   ├── Architecture
│   │   │    ├── projects.cache
│   │   │    ├── modules.cache
│   │   │    └── extensionStorage
│   │   │        └── node-modules-cache
│   │   │            ├── react@18.2.0/
│   │   │            └── react@18.3.1/
│   │   └── hijacks install process
│   │         ├── scanning local registry and use local matches first before downloading any other libraries 
│   │         ├── installing them into the registry to be used in your project. places all new modules in ext 
│   │         ├── folder and registry. Once installation has been completed triggers background process to 
│   │         ├── scan all other projects leveraging the system and matching the registy with the current state
│   │         ├── of each projects package data, ensuring nothing gets stale and libraries that are no longer in use
│   │         └── are removed from your file system
│   │        
│   ├── 📂 CONFIGURATION_AND_MORE/
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#complete-example">Complete Example</a> ............ Production configuration walkthrough
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#usage--previews">Usage & Previews</a> ............ Examples and previews
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#extended-usage-preview"><img src="https://img.shields.io/badge/♠%20Extended%20Usage%20Preview-86198f?style=plastic" valign="middle"></a> ........ Recorded coding session proving zero performance losses
│   │   │    └── despite having 100+ extensions worth of functions.
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#getting-started-w/-chains">Getting Started w/ Chains</a> ... Chain automation guide
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CONFIG_EXAMPLES.md">Config Items Examples</a> ....... Production configuration walkthrough
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#extension-configuration">Extension Configuration</a> ..... Extension settings overview
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#configuration-settings">Configuration Settings</a> ...... Core extension settings
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#core-settings">Core Settings</a> ............... Core extension settings
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#code-snapshot-settings">Code Snapshot Settings</a> ...... Core extension settings
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#github-integration">GitHub Integration</a> .......... Single click multi function operations
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#build--automation-settings">Build & Automation Settings</a> . The lack of non-automation
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#ui--interface-settings">UI & Interface Settings</a> ..... Core extension settings
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#feature-toggles">Feature Toggles</a> ............. Feature flags and toggles 
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#copy-path">Copy Path</a> ................... Path copying utilities
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#reveal-in-explorer">Reveal In Explorer</a> .......... File explorer integration
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#search">Search</a> ...................... Search functionality for config items
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CONFIG.md#edit-json-config">JSON Config Editor</a> .......... Edit .json configs directly
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CONFIG.md#share-config">Share Config</a> ................ Bulk sharing
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CONFIG.md#share-config">Import / Export Config</a> ...... Allows backups, and more
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CONFIG.md#view-config-example">View Config Example</a> ......... Configuration examples
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CONFIG.md#default-apps">Default Apps</a> ................ App configurations
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CONFIG.md#default-apps">ESLint & Prettier Configs</a> ... App configurations
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#remote-resource-mgmt"><img src="https://img.shields.io/badge/♠%20Remote%20Resource%20Mgmt-86198f?style=plastic" valign="middle"></a> ........ Profiles for configs: save/download/edit </span>
│   │   └── 📄<a href="#architecture-notes">Architecture Notes</a> ........... Breaking down the inner workings of the extension
│   │        ├── 📄<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#environment-variable-integration">Env Var Integration</a> ..... using .env vars
│   │        ├── 📄<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#modular-function-building">Modular Func. Building</a> .. Exposing more functions to use
│   │        ├── 📄<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#the-philosophy-of-automation">Automation Principles</a> ... How it came to be 150+ extensions
│   │        ├── 📄<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#the-autorun-system">The Autorun System</a> ...... Help with build processes
│   │        ├── 📄<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#dynamic-package-manager-detection">Dynamic Package Manager</a> . Scan for your package mgr at execution time
│   │        ├── 📄<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#intelligent-terminal-command-engine">Terminal & Command Ngin</a> . The breakdown
│   │        ├── 📄<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#concurrent-and-chain">Concurrent And Chain</a> .... What can be acheived
│   │        ├── 📄<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#autonomous-maintenance">Autonomous Maintenance</a> .. Removing the dev from the equation
│   │        ├── 📄<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#naming-conventions">Naming Conventions</a> ...... So as to not have to include docs, for every single thing
│   │        ├── 📄<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#settings-migration">Settings & Migration</a> .... 
│   │        ├── 📄<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#pro7">pro7</a> .................... Password protected that can be pushed 
│   │        ├── 📄<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#local-encryption">Local Encryption</a> ........ 
│   │        ├── 📄<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#context">Context</a> ................. 
│   │        └── 📄<a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md#vsix-archiver">VSIX Archiver</a> ........... Custom less restrictive archiving tool
│   │  
│   ├── 📂 <a href="https://github.com/8an3/dev-notes/blob/main/docs/CUSTOM_FUNCTIONS.md">CUSTOM_FUNCTION_BREAKDOWNS</a>/
│   │   ├── Order 1 through # ........... Step by step breakdown on executing order #
│   │   └──  ............................
│   │
│   └── 📂 STATUSBAR_AND_CONTEXT_MENU_SYSTEM/
│       ├── 📂 <a href="https://github.com/8an3/dev-notes/blob/main/docs/STATUS_BAR_MENUS.md">STATUS_BAR_DASHBOARDS</a> ....... What you have access to
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/STATUS_BAR_MENUS.md">Clipboard History Pro</a> .... Simply, the windows version vscode
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/STATUS_BAR_MENUS.md">Bookmarks</a> ................ Bookmark anything, anywhere
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/STATUS_BAR_MENUS.md">Icons</a> .................... React icons, inserts at cursor / copies to clipboard
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/STATUS_BAR_MENUS.md">Snapshot Ngin</a> ............ Instant snapshot
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/STATUS_BAR_MENUS.md">UI</a> ....................... Copies to clipboard one of 2500+ components
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/STATUS_BAR_MENUS.md">BE</a> ....................... Bleeding edge features
│       │   └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/STATUS_BAR_MENUS.md">DevStack</a> ................. Main quickpick encompassing a great many of topics
│       ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/EXPLORER_CONTEXT.md">EXPLORER_CONTEXT_MENU</a> ........ Accessing features bound to file type
│       └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/EDITOR_CONTEXT.md">EDITOR_CONTEXT_MENU</a> .......... A treasure trove of functions
│
├── 📂 CATALYST_SOFTWARE/
│   ├──  <a href="https://github.com/8an3/dev-notes/blob/main/docs/LOKI.md"><img src="https://img.shields.io/badge/LOKI%20/-0284c7?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij4KPHBhdGggZD0iTTAgMCBDMC42NiAwIDEuMzIgMCAyIDAgQzIuMjA2MjUgMC45MDc1IDIuNDEyNSAxLjgxNSAyLjYyNSAyLjc1IEM0LjMyMDQwNzkgNi43NTczMjc3NiA2LjI3NTQ5Nzg0IDcuODk0ODQ2NjEgMTAgMTAgQzguODkyNDIzNzggMTIuOTE5OTczNjcgOC4yMjE4NjQxNSAxMy44NzU1Mzk2MiA1LjQzNzUgMTUuNDM3NSBDMi43NDU2OTcxNSAxNi43OTA2MjcxMiAyLjc0NTY5NzE1IDE2Ljc5MDYyNzEyIDIuMTg3NSAxOS42ODc1IEMyLjEyNTYyNSAyMC40NTA2MjUgMi4wNjM3NSAyMS4yMTM3NSAyIDIyIEMxLjM0IDIyIDAuNjggMjIgMCAyMiBDMCAxNC43NCAwIDcuNDggMCAwIFogTTIgOCBDMiA5Ljk4IDIgMTEuOTYgMiAxNCBDMy4zMiAxMy4zNCA0LjY0IDEyLjY4IDYgMTIgQzYgMTEuMzQgNiAxMC42OCA2IDEwIEM0LjY4IDkuMzQgMy4zNiA4LjY4IDIgOCBaICIgZmlsbD0iIzAwMDAwMCIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoNywxKSIvPgo8L3N2Zz4K" valign="middle"></a> ............................ Artificial Intelligence
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CATALYST-UI.md">Deterministic AI Ngin Compiler</a> . Removing 99% of problems you face as a dev when working
│   │   │    └── with prompts
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CATALYST-UI.md"><img src="https://img.shields.io/badge/✓%20LOKI%20Prompt-059669?style=plastic" valign="middle"></a> .................... `A Deterministic AI Engine Compiler` prompt 
│   │   │    └──  and creating a DX that cannot be found anywhere else
│   │   └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CATALYST-UI.md"><img src="https://img.shields.io/badge/✓%20LOKI%20Limitless-059669?style=plastic" valign="middle"></a> ................... Creating outside of the data set
│   │
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CSS.md"><img src="https://img.shields.io/badge/THOR%20/-0284c7?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij4KPHBhdGggZD0iTTAgMCBDMC42NiAwIDEuMzIgMCAyIDAgQzIuMjA2MjUgMC45MDc1IDIuNDEyNSAxLjgxNSAyLjYyNSAyLjc1IEM0LjMyMDQwNzkgNi43NTczMjc3NiA2LjI3NTQ5Nzg0IDcuODk0ODQ2NjEgMTAgMTAgQzguODkyNDIzNzggMTIuOTE5OTczNjcgOC4yMjE4NjQxNSAxMy44NzU1Mzk2MiA1LjQzNzUgMTUuNDM3NSBDMi43NDU2OTcxNSAxNi43OTA2MjcxMiAyLjc0NTY5NzE1IDE2Ljc5MDYyNzEyIDIuMTg3NSAxOS42ODc1IEMyLjEyNTYyNSAyMC40NTA2MjUgMi4wNjM3NSAyMS4yMTM3NSAyIDIyIEMxLjM0IDIyIDAuNjggMjIgMCAyMiBDMCAxNC43NCAwIDcuNDggMCAwIFogTTIgOCBDMiA5Ljk4IDIgMTEuOTYgMiAxNCBDMy4zMiAxMy4zNCA0LjY0IDEyLjY4IDYgMTIgQzYgMTEuMzQgNiAxMC42OCA2IDEwIEM0LjY4IDkuMzQgMy4zNiA4LjY4IDIgOCBaICIgZmlsbD0iIzAwMDAwMCIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoNywxKSIvPgo8L3N2Zz4K" valign="middle"></a> ............................ CSS and Tailwind
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CSS.md">CSS</a> ............................ Put as simply as I can, recreating tailwind but thinking of the
│   │   │    ├── user first. ie, one click installation and configuration of a basic set up 
│   │   │    └── in order to get the user started.
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/THOR.md#tailwind.config.js">tailwind.config.js</a> ............. Creates a basic config file
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/THOR.md#tailwind.config-preset-ngin">tailwind.config Preset Ngin</a> .... 525+ configurations available
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/THOR.md#tailwind.css">tailwind.css</a> ................... Pre-configured CSS file
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/THOR.md#postcss.config.js">postcss.config.js</a> .............. Basic postcss file
│   │   └── 📂 PLUGINS/ ....................... Tailwind Plugin Ngin
│   │       ├── Animation Library ........... One comprehensive solution
│   │       ├── AI/ML UI Patterns............ Modern UI patterns for AI interfaces 
│   │       ├── Framer Motion Helpers........ Tailwind utilities optimized for Framer Motion animations
│   │       ├── Radix UI Integration......... Pre-styled utilities for Radix UI primitives 
│   │       ├── <a href="#untested"><img src="https://img.shields.io/badge/✗%20Tailwind%20PlugIn%20for%20V3%20Users-EF4444?style=plastic" valign="middle"></a> .... Complete v4 feature set in v3 - container queries,  
│   │       │    ├── scroll animations, modern CSS, logical properties, its available for download, but I 
│   │       │    ├── haven't had time to test yet, but will soon because tbh, I'm tired of switching things
│   │       │    └── over from v4 to work in v3. docs but not tested 
│   │       ├── Scrollbar Styles ............ Customizable scrollbar utilities
│   │       ├── Bento Grid Plugin ........... Apple-style bento layouts
│   │       ├── Animated Gradient Borders ... Moving gradient borders (very trendy)
│   │       ├── Neumorphism Plugin .......... Soft UI / Neumorphism styles
│   │       ├── Spotlight Effect Plugin ..... Mouse-following spotlight (like on product pages)
│   │       ├── Glassmorphism ............... Frosted glass effect utilities
│   │       ├── Text Gradients .............. Gradient text utilities
│   │       ├── Custom Animations ........... Additional animation utilities
│   │       ├── Custom Shadows .............. Beautiful shadow utilities
│   │       ├── Background Gradient ......... Beautiful gradient backgrounds
│   │       ├── Aspect Ratios ............... Common aspect ratio utilities
│   │       ├── Glass & Surface Effects ..... Advanced backdrop blurs and reflective surface styles
│   │       ├── Modern Motion & Animation ... High-end animation utilities
│   │       ├── UI Comp Animations Plugin ... accordions, modals, dropdowns
│   │       ├── Attention Grabbers Plugin ... pulse, glow, bounce effects
│   │       ├── Loading States Plugin ....... shimmer, spin, progress
│   │       ├── Interaction Feedback Plugin . click, hover, drag
│   │       ├── Decorative Effects Plugin ... float, wiggle, sway
│   │       ├── Animations Plugin ........... gradients, particles
│   │       ├── Text Effects Plugin ......... typing, reveal, glitch
│   │       ├── Entrance/Exit Ani. Plugin ... accordions, modals, dropdowns
│   │       ├── Matrix/Rain Effect Plugin ... Welcome, Neo...
│   │       ├── Flip Card Plugin ............ Card tricks
│   │       ├── Heartbeat Plugin ............ Heartbeat utilities
│   │       ├── Marquee/Scroll Plugin ....... Marquee utilities
│   │       ├── Ken Burns Plugin ............ Ken Burns utilities zoom and pan
│   │       ├── Entrance Animations Plugin .. Entrance utilities
│   │       ├── Custom Shadows .............. Beautiful shadow utilities
│   │       ├── Background Gradients ........ Beautiful gradient backgrounds
│   │       ├── Aspect Ratios ............... Common aspect ratio utilities
│   │       ├── Border Utilities ............ Advanced border styles
│   │       ├── Scrollbar Plugin ............ Custom Styled scrollbar
│   │       ├── Theme Colors Plugin ......... Extended color palette
│   │       ├── Typography Styles Plugin .... Custom typography styles
│   │       ├── Typography Pro .............. Text balance and fluid headers
│   │       ├── Accordion Animations Plugin . Radix UI Accordion animations
│   │       ├── Caret Blink Plugin .......... Blinking cursor animation
│   │       ├── Glow Animations Plugin ...... Smooth floating animation
│   │       ├── Float Animation Plugin ...... Pulsing glow effects
│   │       ├── Shimmer & Shine Ani. Plugin . Loading shimmer effects
│   │       ├── Spin Animations Plugin ...... Rotation speed animations
│   │       ├── Fade Animations Plugin ...... Fade in/out animations
│   │       ├── Click Animation Plugin ...... Button press feedback
│   │       ├── Movement Animations Plugin .. Horizontal movement animations
│   │       ├── Gradient Flow Plugin ........ Animated gradient background
│   │       ├── Custom Easings Plugin ....... Additional easing functions curves
│   │       ├── Comprehensive Ani. Col. ..... Complete collefction of animations found within the library
│   │       ├── Custom Scrollbar ............ Themed scrollbar
│   │       ├── Skeleton/Placeholder Plugin . Pre-built skeleton components
│   │       ├── Micro-Interactions Plugin ... Subtle micro-interactions
│   │       ├── Spacing & Layout Helpers .... Modern spacing utilities
│   │       ├── Dark Mode Transitions ....... Smooth dark mode transitions plugin
│   │       ├── CSS Grid Helpers ............ Modern grid layouts
│   │       ├── Scroll Animations Plugin .... Scroll-triggered animations
│   │       ├── Focus States Plugin ......... Modern focus styles
│   │       ├── Clamp Utilities Plugin ...... Fluid responsive sizing
│   │       ├── Blend Mode Utilities ........ Modern blend modes
│   │       ├── Noise/Grain Texture Plugin .. Subtle texture overlays
│   │       ├── Container Queries Plugin .... Container query utilities
│   │       ├── 3D Transform Utilities ...... 3D perspective and transforms
│   │       ├── Backdrop Utilities .......... Extended backdrop filters
│   │       ├── CSS Shapes Plugin ........... Pre-made shapes
│   │       ├── Print Utilities ............. Print-specific styles
│   │       ├── Debug Utilities ............. Development helpers
│   │       ├── Architectural Layouts ....... Background patterns
│   │       ├── Masking & Cutouts Plugin .... Advanced CSS masking
│   │       ├── Mobile Safe Area Utilities .. Mobile-specific spacing
│   │       ├── Semantic Surface Depth ...... Inner glows and layered shadows
│   │       ├── Interaction Magnetism ....... Spring-loaded hover states
│   │       └── Border Utilities ............ Advanced border styles
│   │
│   ├── <a href="https://catalyst-software.vercel.app/Catalyst/UI/home/list"><img src="https://img.shields.io/badge/📂%20ICONS%20/-0284c7?style=plastic" valign="middle"></a> ........................... React icon library
│   │   ├── <a href="https://www.npmjs.com/package/@catalystsoftware/icons">Icons NPM Package</a> .............. Package integration
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/ICONS.md">Icons Quick Pick</a> ............... Icon selection tool
│   │   └── <a href="https://catalyst-software.vercel.app/Catalyst/UI/home/list">Icons</a> .......................... Rendered icons provided via library
│   │ 
│   └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CSS.md"><img src="https://img.shields.io/badge/📂%20HEPHAESTUS%20/-0284c7?style=plastic" valign="middle"></a> ...................... React UI components library
│       ├── <img src="https://img.shields.io/badge/❕%20NOTE%20-6b21a8?style=plastic" valign="middle"> Hosts features that are found in the extension and the ui site
│       ├── 📂 VSCode Extension
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CATALYST-UI.md#hephaestus-ui">HEPHAESTUS UI</a> .............. Component library core
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CATALYST-UI.md#editor-context-insert">Editor Context Insert</a> ...... Context menu component insertion
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CATALYST-UI.md#quick-pick-insert">Quick Pick Insert</a> .......... Quick pick component insertion
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CATALYST-UI.md#automated-installation">Automated Installation</a> ..... Install library through extension
│       │   │    └── <a href="https://www.npmjs.com/package/@catalystsoftware/ui">NPM Listing</a> ........... Docs outlining the library
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CATALYST-UI.md#in-editor-comp-autocomplete"><img src="https://img.shields.io/badge/📄%20In%20Editor%20Comp%20Autocomplete%20-0284c7?style=plastic" valign="middle"></a> .. Type '<' followed by the start of the components name 
│       │   │   └── `Bu...` → suggests Button with full docs
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CATALYST-UI.md#smart-prop-autocomplete"><img src="https://img.shields.io/badge/📄%20Smart%20Prop%20Autocomplete%20-0284c7?style=plastic" valign="middle"></a> ..... Shows props with type-aware snippets 
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CATALYST-UI.md#signature-help"><img src="https://img.shields.io/badge/📄%20Signature%20Help%20-0284c7?style=plastic" valign="middle"></a> .............. Live tooltip showing all props as you type inside a 
│       │   │   ├── component's props - providing you with the available parameters/props for each  
│       │   │   └── component as you type 
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CATALYST-UI.md#hover-documentation"><img src="https://img.shields.io/badge/📄%20Hover%20Documentation%20-0284c7?style=plastic" valign="middle"></a> ........ Hover over component for full docs and examples  
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CATALYST-UI.md#auto-import"><img src="https://img.shields.io/badge/📄%20Auto%20import%20-0284c7?style=plastic" valign="middle"></a> ................ Quick fix to add missing imports  
│       │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CATALYST-UI.md#go-to-definition"><img src="https://img.shields.io/badge/📄%20Go%20To%20Definition%20-0284c7?style=plastic" valign="middle"></a> ............. Jump to component source  
│       │   └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CATALYST-UI.md#missing-import-warnings"><img src="https://img.shields.io/badge/📄%20Missing%20import%20warnings%20-0284c7?style=plastic" valign="middle"></a> ...... Diagnostic warnings for imported components 
│       │
│       └── <a href="https://catalyst-software.vercel.app/Catalyst/UI/home/list"><img src="https://img.shields.io/badge/📂%20TOOL_SUITE%20/%20-0284c7?style=plastic" valign="middle"></a> .................... All the tools we use, just in one place
│           ├── VSCode Cmd Reference ........ Built-in command library
│           ├── Markdown Cheat Sheet ........ Web-based reference
│           ├── IRIS: Color Converter ....... Multi-format conversion
│           ├── IRIS: Color Wheel ........... Visual color picker
│           ├── React/Tailwind Sandbox ...... Development playground
│           ├── Theme Builder ............... settings.json & tailwind.css generator
│           ├── Typography Tester ........... Font testing suite
│           ├── Layout Generator ............ UI layout tools
│           ├── X Tester .................... Cross-testing utilities
│           ├── Components Reel ............. Component showcase
│           ├── Tailwind Converter .......... v3 <-> v4, oklch, hsl, 
│           ├── Animation Builder ........... Visual editor
│           ├── Responsive Design Helper .... Breakpoint visualizer
│           ├── Code Carousel ............... Code display tool
│           ├── Sandbox ..................... Live react playground hosting libraries comps
│           ├── Icons ....................... Searchable, Rendered icons
│           ├── RÚNAR Editor ................ Formally catalyst-editor
│           ├── Regex Tester ................ Build and test regex string, cheatsheet included
│           ├── JSON Formatter & Validator .. Sanity check for json files
│           ├── API Response Mocker ......... Mock REST endpoints with custom JSON responses
│           ├── Lorem Ipsum Generator ....... Pick any length and copy to clipboard
│           ├── Cron Expression Builder ..... Visual builder for scheduling cron jobs
│           ├── UUID Hash Generator ......... Generate random hashes in a flash
│           ├── Code Diff Viewer ............ Differences become illuminated
│           ├── Flexbox Sandbox ............. Live preview sandbox featuring flexbox 
│           ├── Grid Sandbox ................ Live preview sandbox feature grid
│           ├── QR Code Generator ........... Images, text, urls 
│           ├── Responsive Preview .......... Test layouts across platforms and breakpoints
│           ├── Accessibility Checker ....... Scan for WCAG compliance and contrast issues
│           ├── Animation Builder ........... Live preview animation builder
│           ├── Chart Playground ............ Build charts, outputing react code to paste
│           ├── MD Badge Builder ............ Quickly build md badges, that render in real time
│           ├── Spinner Generator ........... Build as large of a spinner as you need
│           ├── Terminal Menu Generator ..... Best in class, no limitations terminal menu builder
│           ├── 📂 ENCODER_DECODER_LAB/
│           │   ├── PNG to Base64
│           │   ├── JPG to Base64
│           │   ├── WEBP to Base64
│           │   ├── PDF to Base64
│           │   ├── Base64 to PNG
│           │   ├── Base64 to JPG
│           │   ├── Base64 to WEBP
│           │   ├── Base64 to PDF
│           │   ├── CSV to JSON
│           │   ├── PNG to SVG
│           │   ├── JPG to SVG
│           │   ├── WEBP to SVG
│           │   └── MP4 to MP3
│           │
│           └── <a href="https://catalyst-software.vercel.app/extension/monacoEditor"><img src="https://img.shields.io/badge/📂%20SKÁLD%20/%20-0284c7?style=plastic" valign="middle"></a> ..................... Monaco-level editor
│               ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/SKÁLD.md">Feature Set</a> .............. 150-200+ click-to-clipboard MD features
│               ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/SKÁLD.md">Special Chars</a> ............ HTML and MD style format character list
│               ├── 📂 PRE_MADE_ASSETS/
│               │   ├── File Trees ........... Automated folder visualization
│               │   ├── Progress Bars ........ Markdown progress indicators
│               │   ├── ASCII Tables ......... Pre-formatted tables
│               │   ├── Spinners ............. 17+ different loading spinners
│               │   ├── Terminal Dashboards .. Terminal-style UI layouts
│               │   ├── Code Block Previews .. Code styling previews
│               │   ├── Terminal Menus ....... Visual terminal menu blocks
│               │   ├── Terminal Logs ........ Logs with hierarchy visualization
│               │   ├── Git Branch Viz ....... Branch style visualization
│               │   ├── Status Indicators .... Terminal status boxes
│               │   ├── Notification Boxes ... Terminal notification styling
│               │   ├── Output Separators .... Command output dividers
│               │   ├── Nested Data .......... Nested data structure visualization
│               │   ├── Activity Timeline .... Sequential activity logs
│               │   ├── Terminal Dashboards .. Pre-made dashboards
│               │   ├── Box Drawing .......... Character-based box drawing
│               │   ├── Various Spinners ..... 17 different spinners
│               │   └── Badges and Logos ..... Pre-made badges and icons
│               ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/SKÁLD.md">Readme Generator</a> ......... Feature-rich readme builder
│               ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/SKÁLD.md">Remote Access</a> ............ Connect remotely to workspace MD files
│               └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/SKÁLD.md">Local Settings</a> ........... Locally saved editor settings
│
├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HEIMDALLR.md"><img src="https://img.shields.io/badge/📄%20SAGA%20%20-059669?style=plastic" valign="middle"></a> .................................... To dos, notes, reminders and post it notes
│    └── Recently merged, 2-3 of its least used functions not working
├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HEIMDALLR.md"><img src="https://img.shields.io/badge/📄%20HEIMDALLR%20%20-0284c7?style=plastic" valign="middle"></a> ............................... Intellisense Schema Ngin
├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CONFIG.md#export-index-ngin">Export Index Creator</a> ..................... Export index creator
├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/CONFIG.md#named-export-index-ngin">Named Export Index Creator</a> ............... Named export index creator
├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/WORKSPACE_CONTEXT.md#left-off-note">Left Off Note</a> ............................ Session note tracking
├── <a href="#down"><img src="https://img.shields.io/badge/📄%20HERACLES-0284c7?style=plastic" valign="middle"></a> ............................... Batch Rename - Bulk renaming
├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/UTILS.md#file-nesting"><img src="https://img.shields.io/badge/♦%20File%20Nesting-ca8a04?style=plastic" valign="middle"></a> ............................... Nesting configuration
├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/ARCHIVE.md#vsix-archiver">VSIX Archiver</a> ........................... Custom extension packaging
├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/ARCHIVE.md#vsix-publisher"><img src="https://img.shields.io/badge/📄%20Custom%20.vsix%20publisher-0284c7?style=plastic" valign="middle"></a> .................... Accompanying the above archiver
├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/UTILS.md#region-folding">Region Folding</a> .......................... Fold/toggle region folding
├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/UTILS.md#ratatoskr"><img src="https://img.shields.io/badge/🌲%20RATATOSKR%20-0284c7?style=plastic" valign="middle"></a> ............................. File tree builder & virtualizer 
├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/UTILS.md#ratatoskr"><img src="https://img.shields.io/badge/✓%20Webview%20Creation%20Ngin-059669?style=plastic" valign="middle"></a> ................... Pre-built componets, with their on-clicks, class scafolding 
│   └── code, pre-built commonly used functions and more. Allowing for quicker build times / prototyping 
│
├── 📂 <a href="https://github.com/8an3/dev-notes/blob/main/docs/MARKDOWN.md">MARKDOWN</a>/ 
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/MARKDOWN.md#md-viewer/renderer">MD Viewer/Renderer</a> ................... Standard Markdown viewing
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/MARKDOWN.md#md-viewer-in-vs-code">MD Viewer In VS Code</a> ................. Native VS Code integration
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/MARKDOWN.md#convert-md-to-safe-string">Convert MD to Safe String</a> ............ Markdown to safe inline string
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/MARKDOWN.md#markdown-cheat-sheet">Markdown Cheat Sheet</a> ................. Markdown reference
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/MARKDOWN.md#markdown-pre-processor">Markdown Pre-Processor</a> ............... Converting variables, table structures, toc's
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/BIFRÖST.md"><img src="https://img.shields.io/badge/♠%20Docs%20Viewer-86198f?style=plastic" valign="middle"></a> ........ Integrated Documentation Engine Skip the trip to the VS Code Marketplace   
│   │   ├── or external browsers. BIFRÖST leverages the local documentation shipped directly with the extension
│   │   ├── to provide a high-performance, multi-file viewing experience. By bypassing web latency and the 
│   │   ├── layout limitations of the Marketplace, it delivers a superior UX with custom formatting
│   │   └── tailored specifically for developer workflows.
│
│
├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/RÚNAR.md"><img src="https://img.shields.io/badge/RÚNAR%20/%20-0284c7?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBzdGFuZGFsb25lPSJubyI/Pgo8IURPQ1RZUEUgc3ZnIFBVQkxJQyAiLS8vVzNDLy9EVEQgU1ZHIDIwMDEwOTA0Ly9FTiIKICJodHRwOi8vd3d3LnczLm9yZy9UUi8yMDAxL1JFQy1TVkctMjAwMTA5MDQvRFREL3N2ZzEwLmR0ZCI+CjxzdmcgdmVyc2lvbj0iMS4wIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciCiB3aWR0aD0iMjQuMDAwMDAwcHQiIGhlaWdodD0iMjQuMDAwMDAwcHQiIHZpZXdCb3g9IjAgMCAyNC4wMDAwMDAgMjQuMDAwMDAwIgogcHJlc2VydmVBc3BlY3RSYXRpbz0ieE1pZFlNaWQgbWVldCI+CjxnIHRyYW5zZm9ybT0idHJhbnNsYXRlKDAuMDAwMDAwLDI0LjAwMDAwMCkgc2NhbGUoMC4xMDAwMDAsLTAuMTAwMDAwKSIKZmlsbD0iIzAwMDAwMCIgc3Ryb2tlPSJub25lIj4KPHBhdGggZD0iTTcwIDEyMCBjMCAtNjAgNCAtMTAwIDEwIC0xMDAgNiAwIDEwIDE3IDEwIDM4IGwwIDM3IDM0IC00MCBjMTkgLTIyCjM3IC0zOCA0MCAtMzUgMyAzIC0xMyAyNiAtMzQgNTIgbC00MCA0NiA0MSAyNyA0MSAyNyAtMzggMjQgYy02MiAzOCAtNjQgMzYKLTY0IC03NnogbTcwIDUwIGMwIC00IC0xMSAtMTIgLTI1IC0xOCAtMjQgLTExIC0yNSAtMTAgLTI1IDE4IDAgMjggMSAyOSAyNQoxOCAxNCAtNiAyNSAtMTQgMjUgLTE4eiIvPgo8cGF0aCBkPSJNMjE5IDE3MyBjLTEzIC0xNiAtMTIgLTE3IDQgLTQgMTYgMTMgMjEgMjEgMTMgMjEgLTIgMCAtMTAgLTggLTE3Ci0xN3oiLz4KPC9nPgo8L3N2Zz4K" valign="middle"></a> ................................. Snippets Suite
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/RÚNAR.md"><img src="https://img.shields.io/badge/✓%20Code%20Snapshot-059669?style=plastic" valign="middle"></a> ........................ Snapshot to terminal window 
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/RÚNAR.md#workspace-context">Workspace Context</a> .................... Context-aware code snippets
│   └── <a href="https://catalyst-software.vercel.app/extension/monacoEditor">Snippets Studio</a> ...................... Create / edit snippets. 
│        ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/RÚNAR.md#visit-documentation">Visit documentation</a> ................
│        ├── <a href="https://catalyst-software.vercel.app/extension/monacoEditor">Link to Snippets Editor</a> ............
│        ├── <a href="https://catalyst-software.vercel.app/extension/monacoEditor">Snippet Profiles</a> ...................
│        ├── <a href="https://catalyst-software.vercel.app/extension/monacoEditor">Native Feature Set</a> .................
│        └── <a href="https://catalyst-software.vercel.app/extension/monacoEditor">Remote Access</a> ......................
│
├── 📂 <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md">HUGINN</a>/ ..................................  remix-run utilities
│   ├── 📂 PROJECT_UTILS/
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#npx-create-remixv2">npx create-remixv2</a> ............... Scaffolding engine
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#v1-->-v2-conversion">V1 -> V2 Conversion</a> .............. Routing migration
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#monorepo-conversion">Monorepo Conversion</a> .............. Single app to monorepo
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#create-single-app">Create Single App</a> ................ React Router setup
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#platform-conversion">Platform Conversion</a> .............. Convert to Platform X
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#create-monorepo">Create Monorepo</a> .................. Monorepo scaffolding
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#build--deploy">Build & Deploy</a> ................... Automation workflow
│   │   └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#rr-folder-routing">RR Folder Routing</a> ................ React Router routing logic
│   │
│   ├── 📂 AUTH_UTILITIES/
│   │   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#install-auth">Install Auth</a> ..................... Authentication setup
│   │   └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#install-otp">Install OTP</a> ...................... One-time password setup
│   │
│   └── 📂 ROUTE_UTILITIES/
│       ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#automatic-action">Automatic Action</a> ................. Remix action generator
│       ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#context-utils">Context Utils</a> .................... Components/Functions
│       ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#browser-integration">Browser Integration</a> .............. Open route file in browser
│       ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#route-file-creator">Route File Creator</a> ............... Create route files
│       ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#test-generator">Test Generator</a> ................... Tests for routes/actions
│       ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#code-insertion">Code Insertion</a> ................... Remix Run insert code
│       ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#error-boundary">Error Boundary</a> ................... Error boundary generator
│       ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#meta-function">Meta Function</a> .................... Meta function utility
│       ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#links-function">Links Function</a> ................... Links function utility
│       ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#preview-route">Preview Route</a> .................... Preview route URL
│       └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/HUGINN.md#action-object">Action Object</a> .................... Create action object
│
├── 📂 <a href="https://github.com/8an3/dev-notes/blob/main/docs/MUNINN.md">MUNINN</a>/ .................................. Prisma utilities
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/MUNINN.md#best-practice-guide">Best Practice Guide</a> .................. Prisma best practices
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/MUNINN.md#include-object">Include Object</a> ....................... Create include object
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/MUNINN.md#schema-navigation">Schema Navigation</a> .................... Click to schema object
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/MUNINN.md#crud-resolver-gen">CRUD Resolver Gen</a> .................... Resolvers / REST endpoints
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/MUNINN.md#auto-create-schema">Auto Create Schema</a> ................... Automatic schema generation
│   └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/MUNINN.md#visualizer"><img src="https://img.shields.io/badge/✗%20Visualizer-EF4444?style=plastic" valign="middle"></a> ............................. Schema relations visualization 
│
├── 📂 <a href="https://github.com/8an3/dev-notes/blob/main/docs/SHADCN.md">SHADCN_UI</a>/
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/SHADCN.md#add-components">Add Components</a> ....................... Component addition
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/SHADCN.md#install-w/-config">Install w/ Config</a> .................... Component install with configuration
│   └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/SHADCN.md#insert-components">Insert Components</a> .................... Component insertion
│
├── 📂 <a href="https://github.com/8an3/dev-notes/blob/main/docs/VÖLUNDR.md">VÖLUNDR</a>/ ................................. cleanup / refactoring / automation
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/VÖLUNDR.md#trailing-commas">Trailing Commas</a> ...................... Remove trailing commas
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/VÖLUNDR.md#bragi---comment-killer">BRAGI - Comment Killer</a> ............... Remove all comments
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/VÖLUNDR.md#console.log-killer">Console.log Killer</a> ................... Remove all console.log
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/VÖLUNDR.md#unused-imports">Unused Imports</a> ....................... Remove unused imports
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/VÖLUNDR.md#inline-imports">Inline Imports</a> ....................... Inline imports utility
│   └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/VÖLUNDR.md#json-validator">JSON Validator</a> ....................... Formatting and validation
│
├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/ODIN.md#odin"><img src="https://img.shields.io/badge/ODIN%20/%20-0284c7?style=plastic&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB2ZXJzaW9uPSIxLjEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgd2lkdGg9IjI0IiBoZWlnaHQ9IjI0Ij4KPHBhdGggZD0iTTAgMCBDNy4xNzM5MTMwNCAyLjM5MTMwNDM1IDcuMTczOTEzMDQgMi4zOTEzMDQzNSAxMCA1IEMxMCA1LjY2IDEwIDYuMzIgMTAgNyBDNS4yNSA2LjEyNSA1LjI1IDYuMTI1IDMgNSBDMyA1Ljk5IDMgNi45OCAzIDggQzYuNDY1IDkuOTggNi40NjUgOS45OCAxMCAxMiBDMTAgMTIuOTkgMTAgMTMuOTggMTAgMTUgQzUuMjUgMTMuMTI1IDUuMjUgMTMuMTI1IDMgMTIgQzIuNjcgMTUuMyAyLjM0IDE4LjYgMiAyMiBDMS4zNCAyMiAwLjY4IDIyIDAgMjIgQzAgMTQuNzQgMCA3LjQ4IDAgMCBaICIgZmlsbD0iIzAwMDAwMCIgdHJhbnNmb3JtPSJ0cmFuc2xhdGUoNywxKSIvPgo8L3N2Zz4K" valign="middle"></a> ................................... Search & Discovery
│     ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/ODIN.md#search-editor">Search Editor</a> ....................... Power custom search ngin, expanding on vscodes capabilities
│     │    ├── Remote Editing ................. Make file changes without navigating to the file
│     │    ├── Configurable Searches .......... Create file tree items that trigger preconfigured searchs at will
│     │    ├── Regex History & Helper ......... 
│     │    └── Fuzzy Search ................... 
│     ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/YGGDRASIL.md#file-search-jumper">File Search Jumper</a> ................... Ultra-fast file hopping
│     ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/YGGDRASIL.md#file-line-jumper">File Line Jumper</a> ..................... Jump to specific coordinates
│     └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/YGGDRASIL.md#dependency-deep-link">Dependency "Deep Link"</a> ............... (packageSearch) Jump into node_modules/source
│
├── <details style="display: inline;">│<summary style="cursor: pointer; outline: none; list-style: none; display: inline-block;"><a href="https://github.com/8an3/dev-notes/blob/main/docs/SHORTCUTS.md"><img src="https://img.shields.io/badge/⚡%20SHORTCUT%20MAP-0284c7?style=plastic" style="vertical-align: -6px; margin-top: 1px; margin-bottom: -px;" ></a> ............................. ALT + KEY </summary><div style="margin-top: -30px; line-height: 1.4;"> 
│     ├── [ALT + S] Odin: Search Editor ........ Better-than-native global find
│     ├── [ALT + D] DevStack QP ................ Main Quick Pick Command Palette
│     ├── [ALT + I] Icons ...................... Zap: 525+ search-ready icons
│     ├── [ALT + U] Catalyst UI QP ............. Zap: 2600+ components at cursor
│     ├── [ALT + S] Context Snippets ........... Context-aware code injection
│     ├── [ALT + R] Insert region .............. Surgical code blocking
│     ├── [ALT + E] Insert endregion ........... Close region block
│     ├── [ALT + W] Wrap w/ region ............. Surround selection with logic
│     ├── [ALT + Q] Web UI ..................... Launch External Catalyst Dashboard
│     ├── [ALT + H] History .................... Session & Command history
│     ├── [ALT + B] Bookmarks .................. Enterprise line-level bookmarks
│     ├── [ALT + G] GitHub Menu ................ Deep-link & Repo management
│     ├── [ALT + P] Open Package.json .......... Direct jump to core manifest
│     └── [ALT + M] Open Readme ................ Direct jump to documentation</div></details>│
├── 📂 <a href="https://github.com/8an3/dev-notes/blob/main/docs/FREYR.md">FREYR</a>/ ................................... VSCode styling
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/FREYR.md#blacked-out">Blacked Out</a> .......................... Pre-made black theme 
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/FREYR.md#blued-out">Blued Out</a> ............................ Pre-made blue dark mode theme 
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/FREYR.md#window-differentiator">Window Differentiator</a> ................ Styling differentiation
│   └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/FREYR.md#theme-reset">Theme Reset</a> .......................... Reset window styling
│   
├── 📂 <a href="https://github.com/8an3/dev-notes/blob/main/docs/AUTOMATION_EVENTS.md">VIÐARR/</a> ................................. Automation events
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/AUTOMATION_EVENTS.md#auto-fold-regions">Auto Fold Regions</a> ................... Settings-based folding
│   └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/AUTOMATION_EVENTS.md#forced-editor-groups">Forced Editor Groups</a> ................ Specific group opening
│
├── 📂 <a href="https://github.com/8an3/dev-notes/blob/main/docs/REGEX.md">REGEX</a>/
│    ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/REGEX.md#regex-utilities">Regex Utilities</a> .................... Advanced Regex Lab & tools
│    └── <a href="https://github.com/8an3/dev-notes/blob/main/docs/REGEX.md#regex-cheatsheet">Regex Cheatsheet</a> ................... Reference guide
│
├── 📂 <a href="https://github.com/8an3/dev-notes/blob/main/docs/TYR.md">TÝR</a>/ ................................... Port, process and error utilties
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/TYR.md#portreaper">portReaper</a> .......................... Zombie process killer
│   ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/TYR.md#auto-reaper">Auto Reaper</a> ......................... Automatic cleanup
│   └── <details style="display: inline;"><summary style="cursor: pointer; outline: none; list-style: none; display: inline-block;"><a href="https://github.com/8an3/dev-notes/blob/main/docs/TYR.md#log-to-lens"><img src="https://img.shields.io/badge/♦%200Log%20to%20Lens-ca8a04?style=plastic" style="vertical-align: -6px; margin-top: 1px; margin-bottom: -px;" ></a> ............................. (errorParser) The Pain: Your build failed or your    </summary><div style="margin-top: -15px; line-height: 1.4;"> 
│        ├── test crashed. The terminal is a wall of 500 lines of red text. You have to scroll up, 
│        ├── find the file path in the stack trace, copy it, Ctrl+P, and paste the path to fix the
│        ├── bug. Scans the last output of the integrated terminal for file paths and line numbers.
│        └── It then populates the Navigator with "Jump to Last Error" items. </div></details>│ 
├── 📂 <a href="https://github.com/8an3/dev-notes/blob/main/docs/HERMES.md">HERMES</a>/
│    ├── 📄<a href="https://github.com/8an3/dev-notes/blob/main/docs/ARCHIVE.md#pro7"> Pro7 Archiver</a> ........................... Password protected archive for secrets
│    ├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/UTILS.md#.env-context-swapper">.env Context Swapper</a> .................... (envProfile) Switch environment profiles
│    └── <details style="display: inline;"><summary style="cursor: pointer; outline: none; list-style: none; display: inline-block;"><a href="https://github.com/8an3/dev-notes/blob/main/docs/HERMES.md"><img src="https://img.shields.io/badge/♦%20API%20Secret%20Grabber-ca8a04?style=plastic" style="vertical-align: -6px; margin-top: 1px; margin-bottom: -px;" ></a> ............................. (vaultFetch) You need a staging/prod API   </summary><div style="margin-top: -15px; line-height: 1.4;"> 
│         ├── key that isn't in your local .env for security reasons. You have to log into AWS 
│         ├── Secrets Manager, 1Password, or  your company Wiki, find the key, and copy it.  A type 
│         ├── that fetches a value from a CLI-based vault (like gh secret, aws secretsmanager, or a 
│         ├── local encrypted file). It executes the CLI fetch and uses your existing copyToClipboard
│         └── logic to put the secret in your hand instantly. </div></details>│ 
├── <a href="https://github.com/8an3/dev-notes/blob/main/docs/NEMESIS.md"><img src="https://img.shields.io/badge/📂%20NEMESIS%20/-475569?style=plastic" style="vertical-align: middle; padding-bottom: 2px;"></a>
│     └── <details style="display: inline;"><summary style="cursor: pointer; outline: none; list-style: none; display: inline-block;"><a href="https://github.com/8an3/dev-notes/blob/main/docs/NEMESIS.md"><img src="https://img.shields.io/badge/♦%20Create%20Incoming%20Tunnel-ca8a04?style=plastic" style="vertical-align: -6px; margin-top: 1px; margin-bottom: -px;" ></a> ............................. The Pain: working on a mobile  </summary><div style="margin-top: -15px; line-height: 1.4;"> 
│          └── Detects SQLite by magic bytes (SQLite format 3\0), Not by extension
│              ├── app or an external API that needs to see your local server. You have to open a  
│              ├── separate terminal, remember your ngrok or localtonet command, copy the new URL, 
│              ├── and paste it into your config. It automates the "copy-paste" loop between the 
│              ├── terminal and your code. A specialized command  that launches a tunnel (like ngrok 
│              ├── http 3000), captures the generated URL, and automatically updates a specific 
│              └── line in your config.ts or .env with the new public URL. The Fix: A tunnelLauncher type.</div></details>│ 
└── <img src="https://img.shields.io/badge/📂%20VALHALLA:%20Database%20&%20Storage%20-475569?style=plastic" style="vertical-align: middle; padding-bottom: 2px;">
      └── <details style="display: inline;"><summary style="cursor: pointer; outline: none; list-style: none; display: inline-block;"><a href="https://github.com/8an3/dev-notes/blob/main/docs/VALHALLA.md"><img src="https://img.shields.io/badge/✗%20Sqlite3-EF4444?style=plastic" style="vertical-align: -6px; margin-top: 1px; margin-bottom: -px;" ></a> ............................. Opens editor / viewer in your vscode editor group </summary><div style="margin-top: -15px; line-height: 1.4;"> 
          └── Detects SQLite by magic bytes (SQLite format 3\0), Not by extension
                ├── Opens .vscdb, .random, .whatever
                ├── Built-in presets for common files:
                │    ├── VS Code state.vscdb
                │    ├── Chrome History/Cookies
                │    ├── Firefox places.sqlite
                │    └── etc.
                ├── Instead of a Webview that you have to "Open with...," use the Custom Editor API so that 
                │    └── clicking a .sqlite or .db file opens your UI immediately.
                ├── Keyboard First: Implement Vim-like or Excel-like navigation (arrow keys to move, Ctrl+N 
                │    └── for new row, Del to mark for deletion). 
                ├── Schema Visualizer (ERD): Automatically generate an Entity Relationship Diagram. 
                ├── Notebook Support: Integrate with VS Code's Native Notebooks
                ├── Direct Export to Code: A button that takes a table or query result and generates the code to
                │    └── access it in Python (Pandas), JavaScript (Drizzle/Prisma), or Rust.
                ├── WASM-based Performance: Use a fast WASM build of SQLite
                ├── Transaction Log & Undo: VS Code users expect Ctrl+Z to work.
                └── Extensions Support: Allow users to load SQLite extensions</div></details> 
 

<div class="toc-row">
  <span class="tag tag-folder">📂 TÝR</span> <span>/ Port, process and error utilities</span>
  <div style="margin-left: 20px;">
    <div>portReaper .... Zombie process killer</div>
    <details class="legend">
      <summary class="legend-head">
        <span class="tag tag-planned">Log to Lens</span>
        <span>Automatic Error Parsing</span>
      </summary>
      <div class="legend-content">
        <b class="accent">The Pain:</b> Terminal walls of 500 lines of red text.<br>
        <b class="accent">The Fix:</b> Scans terminal output for stack traces and populates the Navigator with "Jump to Error" items.
      </div>
    </details>
  </div>
</div>

<div class="toc-row">
  <span class="tag tag-folder">📂 VALHALLA</span> <span>/ Database & Storage</span>
  <div style="margin-left: 20px;">
    <details class="legend">
      <summary class="legend-head">
        <span class="tag tag-implemented">SQLite3</span>
        <span>Universal Database Explorer</span>
      </summary>
      <div class="legend-content">
        <div>• <b class="accent">Magic Byte Detection:</b> Opens <code>.vscdb</code>, <code>.db</code>, or extensionless files via binary header.</div>
        <div>• <b class="accent">Custom Editor API:</b> Native VS Code tab experience (no "Open With" menu).</div>
        <div>• <b class="accent">Vim-Flow:</b> Keyboard-first navigation and <code>Ctrl+Z</code> transaction undo.</div>
        <div>• <b class="accent">CodeGen:</b> One-click export to Drizzle, Prisma, or Pandas.</div>
      </div>
    </details>
  </div>
</div>

<div class="toc-row">
  <span class="tag tag-folder">📂 NEMESIS</span> <span>/ Incoming Tunnels</span>
  <div style="margin-left: 20px;">
    <details class="legend">
      <summary class="legend-head">
        <span class="tag tag-planned">TunnelLauncher</span>
        <span>Auto-updating Public URLs</span>
      </summary>
      <div class="legend-content">
        <b class="accent">The Loop:</b> Launches ngrok/localtonet, captures the URL, and <br>
        automatically injects it into your <code>config.ts</code> or <code>.env</code>.
      </div>
    </details>
  </div>
</div>


</pre>













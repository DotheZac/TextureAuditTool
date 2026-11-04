# Texture Audit Tool User Guide

Author: DotheZac · Target: Unreal Engine 5.7, Windows 64-bit · Editor only

## Installation

1. Download a distribution ZIP matching your UE version and platform from [Releases](https://github.com/DotheZac/TextureAuditTool/releases). If no distribution is listed, downloads are not available yet.
2. Close Unreal Editor and extract the archive.
3. Place the `TextureAuditTool` folder inside your project's `Plugins` folder. The descriptor must be at `<Project>/Plugins/TextureAuditTool/TextureAuditTool.uplugin`.
4. Open the project and confirm that `Texture Audit Tool` is enabled in the plugin manager. Restart if prompted.
5. Open `Texture Audit Tool` from the Editor's `Tools` menu.

Distribution ZIPs contain the compiled plugin. GitHub's `Code → Download ZIP` downloads this documentation repository, not an installable plugin. Compatibility with other engine versions or custom source-built engines is not guaranteed. For missing-module or version-mismatch errors, report the archive filename and exact UE version.

## Language

The plugin displays Korean when the Editor language is Korean and English otherwise. Restart the Editor after changing language to apply it consistently to existing windows and scan results. The plugin manager name and description are English.

## Scanning

- `Choose Folder`: choose a Content folder and scan it.
- `Scan Path`: scan a package path such as `/Game/Textures`, or a project Content folder path.
- `Scan Selected Assets`: scan Texture2D assets selected in the Content Browser.
- Use search and priority filters to narrow the results.

## Review priority

| Value | Meaning |
| --- | --- |
| Priority 1 | Review these items first |
| Priority 2 | Review these items next |
| Priority 3 | Review optimization opportunities or intended usage |
| None | No review items were found by the current audit rules |

Priority indicates review order, not danger or the number of changes. `None` does not mean optimal in every environment. Review priority and the availability of automatic recommendations are separate.

## Results and memory

Source Size and Estimated Output are distinct. Recommendations preserve source image files. Editor Format and Editor Allowed Mips come from build data for the current Editor platform and are separate from estimates based on settings. Allowed-mip memory is Fully Loaded GPU memory allowed by the active Device Profile and combined LOD Bias, not the memory of mips currently resident on screen.

Virtual Textures use a shared physical pool, so per-asset GPU memory is not displayed. Editor measurements do not directly represent other target platforms or packaged builds.

## Applying changes

1. Select a result and read its issue causes, proposed changes, expected effects and post-apply checks.
2. Use `Ctrl` or `Shift` to select multiple rows. Details describe the last selected item.
3. Click `Apply Selected Recommendations`, or use the context menu's `Manual Settings`.
4. Read the confirmation and check the result in actual scenes and the Texture Editor after applying.
5. Modified assets are not automatically saved. Save them in the Editor when satisfied, or use `Ctrl+Z` to undo.

Recommendations and manual settings change UE texture properties. Depending on visual quality and material usage, keeping the original settings may be appropriate.

## Review records and shortcuts

- `Modified` is a read-only record of changes applied through the tool.
- Set `Not Reviewed / Needs Review / Reviewed` from the context menu.
- Applying changes defaults the review status to `Reviewed`; this is not automatic visual validation.
- Records are stored in the project's `Config/TextureAuditTool.ini`. Teams can share this file to share records. Preserve it when updating the plugin.
- Resetting records does not revert texture properties.
- Double-click to open a texture. Press `Enter` in the results list to open selected textures.
- Press `F5` in the tool window to refresh results. Results also refresh after Undo/Redo.
- Use the context menu for Reference Viewer, Find in Content Browser, manual settings and review records.

## CSV export

Exports rows visible under the current search and filters, rather than only selected rows. Column names are English; review priority values and audit descriptions follow the Editor language. CSV files include asset names and package paths; review their contents before sharing externally.

## Feedback

Choose a form at [Report a bug or request a feature](https://github.com/DotheZac/TextureAuditTool/issues/new/choose). For installation issues, include the UE version, plugin version and archive filename.

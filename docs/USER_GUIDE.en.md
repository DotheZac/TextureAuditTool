# Texture Audit Tool User Guide

Author: DotheZac · Unreal Engine 5.7 · Windows 64-bit · Editor only

Audit Texture2D settings by folder or path, then apply recommendations or manual settings. The tool stores pre-change properties so they can be restored later.

## Installation and launch

1. Download a distribution ZIP matching your engine version and platform from [Releases](https://github.com/DotheZac/TextureAuditTool/releases). If no distribution is listed, downloads are not available yet.
2. Close Unreal Editor and extract the archive.
3. Place the `TextureAuditTool` folder inside your project's `Plugins` folder. The descriptor must be at `<Project>/Plugins/TextureAuditTool/TextureAuditTool.uplugin`.
4. Open the project and confirm that `Texture Audit Tool` is enabled in the plugin manager. Restart if prompted.
5. Open `Texture Audit Tool` from the Editor's `Tools` menu.

GitHub's `Code → Download ZIP` downloads this documentation repository, not an installable plugin. Distribution binaries target the stated engine version and platform. For missing-module or version-mismatch errors, report the ZIP filename and exact UE version.

## Language

The plugin displays Korean when the Editor language is Korean and English otherwise. Restart the Editor after changing language. The plugin manager name and description are English.

## Scanning and inspecting results

- `Choose Folder`: choose a Content folder and scan it.
- `Scan Path`: scan a package path such as `/Game/Textures`, or a project Content folder path.
- Use search and review-priority filters to narrow the results.
- Select a result to inspect its issue causes, proposed changes, expected effects and post-apply checks.
- Use `Ctrl` or `Shift` to select multiple rows. Details describe the last selected item.

### Review priority

| Value | Meaning |
| --- | --- |
| Priority 1 | Review these items first |
| Priority 2 | Review these items next |
| Priority 3 | Review optimization opportunities or intended usage |
| None | No review items were found by the current audit rules |

Priority indicates review order, not danger or the number of changes. `None` does not mean optimal in every environment. Priority and the availability of automatic recommendations are separate.

### Formats and memory

Source Size and Estimated Output are distinct. Recommendations preserve source image files.

Editor Format and Editor Allowed Mips come from build data for the current Editor platform. Allowed-mip memory is Fully Loaded GPU memory allowed by the active Device Profile and combined LOD Bias, not the memory currently resident on screen. It is separate from estimates based on settings and does not directly represent other platforms or packaged builds.

Virtual Textures use a shared physical pool, so per-asset GPU memory is not displayed.

## Recommendations and manual settings

1. Select results and read the proposed changes and post-apply checks.
2. Click `Apply Selected Recommendations`, or choose `Manual Settings` from the context menu.
3. Review the confirmation, apply changes and check the result in actual scenes and the Texture Editor.
4. Save the assets when satisfied, or use `Ctrl+Z` to undo.

Multiple selected textures can receive the same manual setting at once. Available settings include maximum texture size, compression, Texture Group, mip generation, regular and Virtual Texture streaming, sRGB and Compress Without Alpha.

Changes affect UE texture properties and preserve source images. Assets are not automatically saved. Depending on intended use and visual quality, keeping the original settings may be appropriate.

## Restoring original properties

1. Select one or more textures in the results.
2. Choose `Reset Texture Properties` from the context menu.
3. Read the confirmation and proceed to restore properties saved before the first change by this tool.
4. Check the result and save the assets. Use `Ctrl+Z` to undo the restoration.

**This does not reset textures to engine defaults.** It restores the saved resolution limits, LOD Bias, compression, Texture Group, mip, streaming, color/alpha and build-resizing settings managed by the tool. Source images and import data are preserved.

- Opening the tool or scanning does not save originals. Pre-change values are stored when recommendations or manual settings actually change a texture.
- Repeated changes to the same source retain the first saved values. Restoring properties does not remove these records.
- Items without saved originals, or with a source identifier changed by reimport, are skipped. Changes made before originals were recorded cannot be restored retroactively.
- Restoration also replaces subsequent manual edits to stored properties with their first saved values.
- The Editor may still mark an asset as unsaved after its properties are restored. Save the asset to keep the restored result.

## Modified and review status

Some textures have been reviewed but do not need any changes. In this case, `Modified` remains unchecked while `Review Status` shows `Reviewed`.

- `Modified` is read-only and follows the tool's change records. It is separate from the Editor's unsaved indicator.
- Set `Not Reviewed / Needs Review / Reviewed` from the context menu. Changing review status does not change texture properties.
- Applying recommendations or manual settings defaults the status to `Reviewed`. This is not automatic visual validation; check the texture in actual scenes.
- If current properties differ from the recorded settings, the status may become `Needs Review`.
- `Reset Texture Properties` also restores the modification and review state stored with the originals.
- `Reset Modification and Review History` removes the display records. Texture properties and saved originals are preserved.

## Records stored in your project

| File | Contents |
| --- | --- |
| `Config/TextureAuditTool.ini` | Modification/review records and state tracking for Undo/Redo display |
| `Config/TextureAuditToolOriginalSettings.ini` | Values saved before the first change, used for restoration |

Both files are stored in the consuming project's `Config`. Teams can share these files to use the same records. Preserve them during plugin updates. Do not include your project's records when distributing the plugin to other projects.

## Opening assets and refreshing

| Action | Usage |
| --- | --- |
| Open textures | Double-click a result, or select results and press `Enter` in the list |
| Inspect references | Context menu → `Reference Viewer` |
| Locate assets | Context menu → `Find in Content Browser` |
| Rescan current results | Press `F5` in the tool window |
| Undo/Redo changes | Use the Editor's Undo/Redo; results refresh afterwards |

## CSV export

Exports rows visible under the current search and filters, rather than only selected rows. Column names are English; review priority values and audit descriptions follow the Editor language. CSV files include asset names and package paths; review their contents before sharing externally.

## Feedback

Choose a form at [Report a bug or request a feature](https://github.com/DotheZac/TextureAuditTool/issues/new/choose). For installation issues, include the UE version, plugin version and ZIP filename.

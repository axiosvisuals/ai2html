# ai2svelte

A version of [ai2html](https://github.com/newsdev/ai2html) designed specifically to output Svelte components from AI files. Heavily informed by the [Reuters Graphics](https://github.com/reuters-graphics/ai2svelte) team's work on this.

## How to use

1. Make sure you have both `ai2svelte.js` and `ai2html-config.json` in your `Applications/[Adobe Illustrator]/Presets/en_US/Scripts` directory
2. Copy the [ai2svelte](https://drive.google.com/drive/folders/1ya6nyGzHvoGcgkbvmyplePwqdBGuSCYZ) template from the team Drive folder to your project.
3. Rename the folder and the `yyyy-mm-dd-slug.ai` folder. The name of the `.ai` file will be the name of the Svelte component, so we recommend using title-case naming (eg. `WorldMap.ai`).
4. Create your graphics using the artboards provided. Feel free to create more as needed.

- **Note:** We recommend **not** including the hed or dek of the chart in the Artboard. Instead, you can set it in Svelte.

5. When you're ready, run `ai2svelte` (File --> Scripts --> ai2svelte)
6. When the script runs, you should see an `/output` directory in the folder that contains:

- `[Slug].svelte` - your Svelte component
- `/images/` - Images directory that contains all the images needed for the graphic

7. Copy the `/output` directory to your components directory in your Svelte project and rename accordingly.
8. Import the AI component and use in your project

```svelte
<script>
  import WorldMap.svelte from "components/WorldMap/WorldMap.svelte`
</script>

<WorldMap />
```

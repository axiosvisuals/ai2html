# ai2svelte

A version of [ai2html](https://github.com/newsdev/ai2html) designed specifically to output Svelte components from AI files. Heavily informed by the [Reuters Graphics](https://github.com/reuters-graphics/ai2svelte) team's work on this.

## How to use

1. Make sure you have both `ai2svelte.js` and `ai2html-config.json` in your `Applications/[Adobe Illustrator]/Presets/en_US/Scripts` directory
2. Copy the [ai2svelte](https://drive.google.com/drive/folders/1ya6nyGzHvoGcgkbvmyplePwqdBGuSCYZ) template from the team Drive folder to your project.
3. Rename the folder and the `yyyy-mm-dd-slug.ai` folder. The name of the `.ai` file will be the name of the Svelte component, so we recommend using title-case naming (eg. `WorldMap.ai`).
4. Create your graphics using the artboards provided. Feel free to create more as needed.

- **Note:** We recommend **not** including the hed or dek of the chart in the Artboard. Instead, you can set it in Svelte.

5. When you're ready, run `ai2svelte` (File --> Scripts --> ai2svelte)
6. When the script runs, you should see a new directory titled `/[slug]` in the folder that contains:

- `[Slug].svelte` - your Svelte component
- `/images/` - Images directory that contains all the images needed for the graphic

7. Copy the `/[slug]` output directory to your components directory in your Svelte project and rename accordingly. Depending on your project structure, that might look like `/src/lib/components/`.
8. Import the AI component and use in your project

```svelte
<script>
  import WorldMap.svelte from "components/WorldMap/WorldMap.svelte"
</script>

<WorldMap />
```

## Modifying settings

If you need to modify any of the default settings, you can do so by creating an `ai2html-config.json` file in your project folder or by modifying the `ai2html-settings` block in the `.ai` file. See [ai2html.org](http://ai2html.org/#settings) for details.

### Custom fonts

To add custom fonts to a project, we recommend using an `ai2html-config.json` file. To use a custom font, add the font information to the `fonts` array, like this:

`ai2html-config.json`

```txt
{
  "fonts": [
    {
      "aifont": "CCMeanwhile",
      "family": "ccmeanwhile, sans-serif",
      "weight": "",
      "style": ""
    }
  ]
}

```

Save `ai2html-config.json` to the same directory as your `.ai` file.

In order to add fonts to the array, you'll need to know the Illustrator name for the font files. If you haven't already, save [`/utilities/aifontname.js`](https://github.com/axiosvisuals/ai2html/blob/main/utilities/aifontname.js) to `Applications/[Adobe Illustrator]/Presets/en_US/Scripts`.

With your `.ai` file open in Illustrator, go to `File --> Scripts --> aifontname`. This will generate a popup in AI of the fonts used. These are the names you want to use in the `fonts` array.

#### Fonts from Adobe Fonts/Google Fonts

If you're loading in fonts from Adobe Fonts/Typekit/Google Fonts, you must also:

1. Add fonts to Creative Cloud (Adobe Fonts only)
   1. Sign in to https://fonts.adobe.com
   2. Find the custom fonts needed for the project and mark them as "active". This should sync them to your local computer using Creative Cloud.
   3. Add to or create a new Web Project
      - **Note:** Only include the fonts/font weights you'll actually be using in the Web Project. Every new font/weight/style increases the overall page load time. This is different from the fonts you have active on your local computer.
2. In your Svelte project, add the embed code provided by Adobe Fonts

```
<link rel="stylesheet" href="https://use.typekit.net/vlt1eba.css">
```

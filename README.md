## How to get it working

First you will need to have a Vercel account or any other quick deploy tool, vercel is recommended tho.
After just connect to the repository and you should be able to start populating your world wiki.

### Running the project

With node already installed, run

```
npm run install
```

Now run the project with

```
npm run dev
```

The defaul local URL is localhost:3000.

## Customizing the app
First file to modify is [config/site.ts](config/site.ts). Update the site title, description, contact email and any branding values there.

Below are clear steps and examples to create pages and customize the app.

## Creating pages

Use the project helper to scaffold a new wiki page folder and files:

`npm run create-page -- <slug> [title] [--type <type>] [--skip-router]`

- `slug`: folder name and URL (e.g. `araleth`). Required.
- `title` (optional): human-friendly page title. Defaults to a capitalized version of the slug.
- `--type <type>` (optional): populates `info.json` from a template. Available types: `character`, `location`, `god` (see `scripts/page-templates`).
- `--skip-router` (optional): create files only and do not update `router.json`.

Examples:

- Create a character page and register it in the router:

	`npm run create-page -- araleth "Araleth Silverleaf" --type character`

- Create a location page without modifying the router:

	`npm run create-page -- ironhold "Ironhold" --type location --skip-router`

What the script creates:

- `content/pages/<slug>/content.md` — the Markdown content for the page.
- `content/pages/<slug>/info.json` — structured metadata (title plus any template fields).
- `content/pages/<slug>/images/` — image folder (a `.gitkeep` file is added).

The available info templates are located at `scripts/page-templates/` and include `character-info.json`, `location-info.json`, and `god-info.json`.

After creating pages you can run the validator to refresh the site manifest:

`npm run validate-wiki`

## Page content structure

A page folder looks like:

- `content/pages/<page-name>/`
	- `content.md`
	- `info.json`
	- `images/`
		- `portrait.png` (or jpg/jpeg)

Use `##` headings in `content.md` to create sections.

To include an image in Markdown (left or right hint):

```
![right](portrait.png)
```

## Customizing the app (examples)

- Site metadata: edit [config/site.ts](config/site.ts) to change name, description and contact info.
- Page templates: edit or add templates in `scripts/page-templates/*.json` to provide default `info.json` fields for new pages.
- Router: `router.json` controls the visible pages and order. The create script adds entries automatically unless you use `--skip-router`.
- Images: upload image files into the page `images/` folder and reference them from `content.md`.
- Theme: the app uses `next-themes` and Tailwind. Quick theme tweak points:
	- edit `styles/globals.css` to adjust global styles
	- edit `tailwind.config.js` to change color tokens

If you want, I can also add a short example showing how to change the site title and add a new page end-to-end. Which would you prefer next?

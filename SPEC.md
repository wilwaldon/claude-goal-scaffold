# Site Specification

## How to Use This File

Write every requirement so Claude can prove it's done by running a command or showing output. If you can't describe how to verify it, Claude can't either, and the /goal evaluator will keep the loop running.

Bad: "The homepage should look nice and be engaging."
Good: "The homepage has a hero section with headline, subheadline, and a CTA button linking to /pricing."

Bad: "Add some products."
Good: "The products page renders a grid of cards from src/data/products.json. Each card shows name, price, and category. Minimum 8 products in the data file."

## Global Components

### Header
- [Logo: text-based or image reference]
- [Nav links: list every page by name and path]
- [CTA button: text and destination]
- [Mobile behavior: hamburger menu below what breakpoint?]

### Footer
- [What goes here: address, links, social icons, newsletter signup?]
- [Legal: copyright line, privacy/terms links?]

## Pages

[Copy this block for each page. Delete the comments when you fill it in.]

### [Page Name] (`/[route]`)

**Sections** (top to bottom):
1. [Section name]: [What it contains. What data source it reads from. What interactive behavior it has, if any.]
2. [Section name]: [Same level of detail.]
3. [Section name]: [Keep going until the page is fully described.]

**Behavior:**
- [Any client-side interactivity: filters, tabs, accordions, form submissions]
- [What happens on submit/click? Console.log? Navigate? Show a toast?]

**Data source:** `src/data/[filename].json`

---

[EXAMPLE PAGES -- delete these and write your own]

### Homepage (`/`)

**Sections:**
1. Hero: Headline, subheadline, CTA button linking to /[your main page]
2. Features: 3-4 cards. Each has an icon (use an emoji or SVG placeholder), title, and one-sentence description. Data from `src/data/features.json`
3. Social proof: A short quote with attribution. Hardcoded is fine.
4. CTA banner: Repeated call to action before the footer.

**Behavior:** No interactivity. Static content.

### [Second page] (`/[route]`)

**Sections:**
1. [Describe it]

**Behavior:**
- [Describe it]

**Data source:** `src/data/[file].json`

---

## Data Files

[List every JSON file Claude needs to create. Specify the shape.]

```
src/data/features.json
[
  {
    "id": "string",
    "title": "string",
    "description": "string",
    "icon": "string (emoji)"
  }
]
```

[Repeat for each data file. If you don't specify the schema, Claude will invent one and you'll spend turns correcting it.]

## What "Done" Looks Like

[This section feeds directly into your /goal command. Write it as a checklist.]

- [ ] All [N] pages render at their defined routes
- [ ] All data files exist in src/data/ with realistic sample content
- [ ] Navigation works between every page
- [ ] [Any interactive feature] works as specified
- [ ] npm run build exits 0 with no TypeScript errors
- [ ] npm run dev starts without errors

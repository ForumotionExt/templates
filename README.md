# ForumotionExt / templates

Backup of the **default Forumotion templates**, organised by category and numeric ID.  
Used by the [ForumotionExt browser extension](https://github.com/ForumotionExt/forumotion-extension) to provide a reference copy of every stock template so users can compare or restore their customisations.

---

## Repository structure

```
index.json          ← full catalogue (categories + template metadata)
catalog/
  main/             ← General / main category
    110.html        index_body
    111.html        index_box
    113.html        memberlist_body
    114.html        message_body
    115.html        overall_footer_begin
    116.html        overall_header
    118.html        search_body
    125.html        viewforum_body
    126.html        viewonline_body
    127.html        viewtopic_body
    130.html        topics_blog_box
    131.html        viewcomments_body
    133.html        overall_footer_end
  portal/           ← Portal category
  gallery/          ← Gallery category
  calendar/         ← Calendar category
  group/            ← Groups category
  post/             ← Post & Private Messages category
  moderation/       ← Moderation category
  profil/           ← Profile category
  mobile/           ← Mobile category
```

Each HTML file is a raw Forumotion phpBB3 template and uses the standard Forumotion template-variable syntax:

| Syntax | Meaning |
|--------|---------|
| `{VARIABLE}` | Simple scalar variable |
| `<!-- BEGIN block_name -->…<!-- END block_name -->` | Conditional / loop block |
| `{block.VARIABLE}` | Variable scoped inside a block |

---

## index.json

`index.json` at the root is the machine-readable catalogue consumed by the extension.  
Top-level fields:

| Field | Type | Description |
|-------|------|-------------|
| `version` | `number` | Schema version (currently `1`) |
| `categories` | `array` | All supported template categories (`key`, `label`) |
| `templates` | `array` | All backed-up templates (see below) |

Each entry in `templates`:

| Field | Type | Description |
|-------|------|-------------|
| `id` | `string` | Numeric template ID as used in the Forumotion admin panel |
| `label` | `string` | Template internal name (e.g. `overall_header`) |
| `description` | `string` | Short description of what the template renders |
| `category` | `string` | Category key (matches `categories[].key`) |
| `file` | `string` | Relative path to the HTML file |

---

## Template categories

| Key | Label | Notes |
|-----|-------|-------|
| `main` | General | Core page templates (header, footer, index, topic…) |
| `portal` | Portal | Portal module templates |
| `gallery` | Gallery | Photo gallery templates |
| `calendar` | Calendar | Events calendar templates |
| `group` | Groups | Group management templates |
| `post` | Post & Private Messages | Posting form and PM templates |
| `moderation` | Moderation | Moderation panel templates |
| `profil` | Profile | User profile templates |
| `mobile` | Mobile | Mobile-specific templates |

---

## Contributing

To add templates for other categories, place the HTML file under `catalog/{category}/{id}.html` and add a corresponding entry to `index.json`.

---

## Related repositories

| Repository | Description |
|-----------|-------------|
| [ForumotionExt/forumotion-extension](https://github.com/ForumotionExt/forumotion-extension) | Chrome extension that uses this template backup |
| [ForumotionExt/forumotion-themes](https://github.com/ForumotionExt/forumotion-themes) | Catalogue of custom Forumotion themes |

---
title: "Your First Collection"
weight: 3
bookToc: true
---

# Your First Collection

## What Is a Collection?

A **collection** is simply a folder of markdown files that you want QMD to search. You might have separate collections for:

- Personal notes
- Work documents
- Meeting transcripts
- Project documentation

## Adding a Collection

Let's say you have notes in `~/notes`. To add them as a collection:

```sh
qmd collection add ~/notes --name notes
```

That's it! QMD will scan the folder and index all markdown files it finds.

## Adding More Collections

You can add as many collections as you want:

```sh
qmd collection add ~/Documents/meetings --name meetings
qmd collection add ~/work/docs --name docs
```

## Custom File Patterns

By default, QMD looks for `**/*.md` files. If you want to include other patterns:

```sh
qmd collection add ~/docs --name docs --mask "**/*.md"
```

## List Your Collections

To see all your collections:

```sh
qmd collection list
```

## Remove a Collection

If you no longer want to search a folder:

```sh
qmd collection remove notes
```

This only removes the collection from QMD's index — your files are not touched.

## Rename a Collection

```sh
qmd collection rename notes my-notes
```

## Browse Collection Files

To see what files QMD found in a collection:

```sh
qmd ls notes
qmd ls notes/subfolder
```

## Update the Index

When you add or change files, update the index:

```sh
qmd update
```

## Practice Exercise

1. Create a folder with a few markdown files
2. Add it as a collection
3. Run `qmd collection list` to verify
4. Run `qmd ls <your-collection>` to see the files

## Next Steps

Your documents are indexed! Now let's learn how to search them.

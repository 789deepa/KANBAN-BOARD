# Kanban Board

A lightweight, browser-based Kanban board for organizing tasks across **To Do**, **In Progress**, and **Done**. Add tasks with a title and description, drag them between columns as work progresses, and remove them when they are no longer needed.

## Features

- Three workflow columns with live task counts
- Add tasks using the **Add New Task** dialog
- Drag and drop tasks between columns
- Delete tasks from the board
- Automatically save and restore tasks with browser `localStorage`
- Dark, responsive-friendly interface built with plain HTML, CSS, and JavaScript

## Getting started

No package installation or build step is required.

1. Clone or download this repository.
2. Open `index.html` in a modern web browser.

For a more consistent local development experience, serve the project using a local static web server (for example, the **Live Server** extension in Visual Studio Code) and open the local URL it provides.

## Using the board

1. Select **Add New Task**.
2. Enter a task title and optional description, then select **Add Task**.
3. Drag a task card into **In Progress** or **Done** as its status changes. You can also move it back to an earlier column.
4. Select **Delete** on a card to remove it.

The number in each column heading shows how many tasks it contains.

## Saving tasks

The board saves its tasks in the browser's `localStorage`. Your tasks remain available after a refresh in the same browser profile, but they are not synced across browsers or devices. Clearing the browser's site data will remove the saved board.

## Project files

| File | Purpose |
| --- | --- |
| `index.html` | Board layout, columns, and add-task dialog |
| `style.css` | Layout, colors, and component styling |
| `app.js` | Task creation, drag and drop, counts, and local persistence |
| `image.png` | Project image asset |
| `Notes.md` | Development notes about the implementation |

## Built with

- HTML
- CSS
- Vanilla JavaScript
- Browser `localStorage` and native drag-and-drop events

===============================
KANBAN PROJECT — NOTES
===============================

1) PROJECT STRUCTURE
--------------------
This project was divided into two main parts:
1. Navbar
2. Columns (To-Do, Progress, Done)

Before anything else:
- Made basic HTML structure
- Linked CSS
- Created main layout (nav + section)


2) NAVBAR SETUP
----------------
Navbar = two sides:
- Left → "Kanban" text
- Right → "Add New Task" button

Simple two-div structure inside <nav>.


3) COLUMNS SETUP
-----------------
Inside <section class="board">, I created:
- #todo
- #progress
- #done

Each column has:
- heading (title + count)
- space for tasks

Also created :root variables in CSS for colors.


4) TASK STYLING BASICS
-----------------------
Made a .task class for each task.

Example structure:
<div draggable="true" class="task">
    <h2>Title</h2>
    <p>Description</p>
    <button>Delete</button>
</div>

To move delete button to bottom:
align-self: flex-end;


5) DRAG & DROP — CORE LOGIC
----------------------------
Goal: highlight column while dragging over it.

Steps:
1. Add draggable="true" to tasks
2. Make a .hover-over class in CSS for highlighting
3. Add event listeners:
   - dragenter → highlight column
   - dragleave → remove highlight
   - dragover → allow dropping
   - drop → drop task in column

Example:
column.addEventListener("dragenter", function(e){
    this.classList.add("hover-over");
});

dragover MUST contain e.preventDefault()
because browser blocks dropping by default.

To avoid repeating code for each column,
I created a reusable function:
addDragEventsOnColumn(column)


6) appendChild() — MAIN DROP ACTION
------------------------------------
On drop:
column.appendChild(dragElement);

This physically moves the dragged task div
into whichever column was dropped on.


7) ADD NEW TASK — MODAL SYSTEM
-------------------------------
Created a modal:
<div class="modal">
    <div class="bg"></div>
    <div class="center">...</div>
</div>

- modal.active { display: flex }
- backdrop-filter: blur(3px) on .modal .bg for background blur

Modal opens on "Add New Task" button.
Modal closes when clicking background.


8) CREATING TASK DYNAMICALLY
-----------------------------
addTask(title, desc, column) does:
- creates new .task div
- sets draggable
- adds delete button logic
- appends to the selected column

Every new task instantly becomes draggable.


9) LOCAL STORAGE — SAVE EVERYTHING
-----------------------------------
Goal: board should remember tasks after refresh.

Steps:
1. Create tasksData object:
   let tasksData = {};

2. In updateTaskCount():
   tasksData[col.id] = Array.from(tasks).map(task => ({
       title: task.querySelector("h2").innerText,
       desc: task.querySelector("p").innerText
   }));

3. Save to localStorage:
   localStorage.setItem("tasks", JSON.stringify(tasksData));

4. On load:
   Read saved data:
   const data = JSON.parse(localStorage.getItem("tasks"));

   Loop through each saved column:
   addTask(task.title, task.desc, column);


10) FINAL FIXES MADE
---------------------
- Corrected columns.appendChild → column.appendChild
- Fixed typos in IDs (add-new-task)
- Ensured new tasks get drag listeners
- Prevented hover flickering
- Corrected task counts
- Aligned modal styling properly


11) WHAT I LEARNED
-------------------
This project helped me understand:
- Real drag & drop logic
- Structuring a JS project cleanly
- Reusable functions
- Saving UI state using localStorage
- Debugging DOM issues
- How small typos break big features

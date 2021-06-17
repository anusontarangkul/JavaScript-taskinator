# Taskinator

A kanban board app organizing your tasks.

![gif](./assets/screenshot/gif.gif)

### Features

- Enter Task Name
- Pick a task type
- Update tasks with "to do", "in progress", or "completed"
- Data is stored and loaded to local storage
- Edit tasks
- Delete tasks

## Table of Contents

|                                         |                                                               |                                                   |
| :-------------------------------------: | :-----------------------------------------------------------: | :-----------------------------------------------: |
|   [Project Introduction](#Taskinator)   |            [Table of Contents](#table-of-contents)            | [Development Highlights](#development-highlights) |
|         [Deployment](#deployed)         | [Description of Page Building](#Description-of-Page-Building) |       [Code Hightlights](#code-highlights)        |
| [Technologies Used](#Technologies-Used) |                      [Credits](#Credits)                      |                [License](#License)                |

## Development Highlights

- Use DOM methods such as `addEventListener()`, `querySelector()`, `createElement()`, `setAttribute()`, and `getAttribute()`.
- Interactive HTML by using `click`, `submit`, and `change` event listeners.
- Use the `event` object.
- Using `JSON.stringify()` and `JSON.parse()` to save and load data from `localStorage `.

## Deployment

[Deployment](https://anusontarangkul.github.io/taskinator/)

This app is deployed using GitHub pages.

## Description of Page Building

- assets
  - css
  - images
  - js
  - screenshots
- .gitignore
- index.html
- LICENSE
- README

## Code Highlights

Use the `event.target` to find the element selected and then find the attribute `data-task-id` to edit or delete specific tasks.

```
var taskButtonHandler = function (event) {
// get target element from event
var targetEl = event.target;

    // edit button was clicked
    if (targetEl.matches(".edit-btn")) {
        var taskId = targetEl.getAttribute("data-task-id");
        editTask(taskId)
    }

    if (event.target.matches(".delete-btn")) {
        var taskId = event.target.getAttribute("data-task-id");
        deleteTask(taskId);
    }
}
```

Because we store the tasks in an object, we turn in into a string so the data can be saved in local storage.

```
var saveTasks = function () {
    localStorage.setItem("tasks", JSON.stringify(tasks));
}
```

Loading the data from the local storage when the app opens. The data comes in a string so we need to parse into an object.

```
var loadTasks = function () {
    var savedTasks = localStorage.getItem("tasks");

    if (!savedTasks) {
        return false;
    };

    savedTasks = JSON.parse(savedTasks);

    for (var i = 0; i < savedTasks.length; i++) {
        //  pass each task object into the `createTaskEl()`
        createTaskEl(savedTasks[i]);
    }

}
```

## Technologies Used

- [HTML](https://www.w3schools.com/html/)
- [JavaScript](https://www.javascript.com/)
- [CSS](https://www.w3schools.com/css/)

## Credits

|                           |                                                                                                                                                                                                       |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **David Anusontarangkul** | [![Linkedin](https://i.stack.imgur.com/gVE0j.png) LinkedIn](https://www.linkedin.com/in/anusontarangkul/) [![GitHub](https://i.stack.imgur.com/tskMh.png) GitHub](https://github.com/anusontarangkul) |

The CSS styling for this app was provided.

## License

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

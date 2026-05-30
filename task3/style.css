const taskInput = document.getElementById("task-input");
const addBtn = document.getElementById("add-btn");
const taskList = document.getElementById("task-list");
const filterButtons = document.querySelectorAll(".filter-btn");

let tasks = JSON.parse(localStorage.getItem("tasks")) || [];

/* SAVE TO LOCAL STORAGE */
function saveTasks() {
  localStorage.setItem("tasks", JSON.stringify(tasks));
}

/* DISPLAY TASKS */
function renderTasks(filter = "all") {

  taskList.innerHTML = "";

  let filteredTasks = tasks;

  if (filter === "active") {
    filteredTasks = tasks.filter(task => !task.completed);
  }

  if (filter === "completed") {
    filteredTasks = tasks.filter(task => task.completed);
  }

  filteredTasks.forEach(task => {

    const li = document.createElement("li");
    li.classList.add("task-item");

    if (task.completed) {
      li.classList.add("completed");
    }

    li.innerHTML = `
      <span>${task.text}</span>

      <div class="task-buttons">

        <button class="edit-btn">
          Edit
        </button>

        <button class="delete-btn">
          Delete
        </button>

      </div>
    `;

    /* TOGGLE COMPLETE */
    li.addEventListener("click", () => {
      task.completed = !task.completed;
      saveTasks();
      renderTasks(filter);
    });

    /* DELETE TASK */
    li.querySelector(".delete-btn")
      .addEventListener("click", (e) => {

      e.stopPropagation();

      tasks = tasks.filter(t => t.id !== task.id);

      saveTasks();
      renderTasks(filter);

    });

    /* EDIT TASK */
    li.querySelector(".edit-btn")
      .addEventListener("click", (e) => {

      e.stopPropagation();

      const updatedText = prompt("Edit task:", task.text);

      if (updatedText !== null) {
        task.text = updatedText;
        saveTasks();
        renderTasks(filter);
      }

    });

    taskList.appendChild(li);

  });
}

/* ADD TASK */
addBtn.addEventListener("click", () => {

  const text = taskInput.value.trim();

  if (text === "") return;

  const newTask = {
    id: Date.now(),
    text: text,
    completed: false
  };

  tasks.push(newTask);

  saveTasks();
  renderTasks();

  taskInput.value = "";

});

/* FILTER BUTTONS */
filterButtons.forEach(button => {

  button.addEventListener("click", () => {

    const filter = button.dataset.filter;

    renderTasks(filter);

  });

});

/* INITIAL LOAD */
renderTasks();

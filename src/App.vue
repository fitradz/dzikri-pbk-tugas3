<template>
  <div id="app" class="dark-mode">
    <h1>Ketikan Tujuan</h1>
    <div class="input-container">
      <input v-model="newTask" placeholder="Tambahkan tugas baru" />
      <button @click="addTask" class="add-btn">Tambah</button>
    </div>
    <ul>
      <li v-for="(task, index) in tasks" :key="index" class="task-item">
        {{ task.text }}
        <div class="actions">
          <button @click="editTask(index)" class="edit-btn">Edit</button>
          <button @click="removeTask(index)" class="delete-btn">Hapus</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      newTask: '',
      tasks: []
    }
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== '') {
        this.tasks.push({ text: this.newTask.trim() })
        this.newTask = ''
      }
    },
    editTask(index) {
      const newText = prompt('Ubah tugas:', this.tasks[index].text)
      if (newText !== null && newText.trim() !== '') {
        this.tasks[index].text = newText.trim()
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1)
    }
  }
}
</script>

<style>
body {
  font-family: Arial, sans-serif;
  background-color: #000;
  color: #fff;
}

#app.dark-mode {
  max-width: 500px;
  margin: 0 auto;
  padding: 20px;
  background-color: #121212;
  box-shadow: 0 2px 4px rgba(255, 255, 255, 0.1);
}

h1 {
  text-align: center;
  color: #fff;
}

.input-container {
  display: flex;
  margin-bottom: 20px;
}

input[type="text"] {
  flex: 1;
  padding: 10px;
  border: 1px solid #333;
  border-radius: 4px;
  background-color: #121212;
  color: #fff;
}

.add-btn {
  margin-left: 10px;
  padding: 10px 20px;
  background-color: #4caf50;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  border-bottom: 1px solid #333;
  background-color: #121212;
  color: #fff;
}

.actions {
  display: flex;
}

.edit-btn,
.delete-btn {
  margin-left: 10px;
  padding: 5px 10px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  color: #fff;
}

.edit-btn {
  background-color: #2196f3;
}

.delete-btn {
  background-color: #f44336;
}
</style>
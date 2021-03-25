<template>
  <div>
    <h1>Minha lista de tarefas!</h1>
    <button @click="handleShowHidelist">Ver a lista!</button>
    <br>
    <input 
      type="text" 
      @keyup.enter="addTask"
      v-focus 
      v-model="currentTask"
    >
    <ul v-if="showList">
      <li 
        v-for="(task, index) in tasks"
        @dblclick="complete(task)"
        :key="`${task}-${index}`"
        :class="{'line-through': task.isDone}"
      >
        {{ task.name }}
        <button
          @click="remove(task)"        
        >&times;</button>
      </li>
    </ul>
    <p v-else>Lista de tarefas escondidas</p>
  </div>
</template>

<script>
const focus = {
    inserted: (el) => {
      el.focus()
    }
}
export default {
  directives: {
    focus,
  },
  data: () => ({
    currentTask: '',
    showList: false,
    tasks: [
      { name: 'Fazer o curso', isDone: false}
    ]
  }),
  methods: {
    addTask () {
      this.tasks.push({
        name: this.currentTask,
        isDone: false
      })
      this.currentTask = ''
    },
    remove (task) {
      this.tasks = this.tasks.filter(t => t.name !== task.name)
    },
    complete (task) {
      this.tasks = this.tasks.map(t => {
        if (t.name === task.name) {
          return { ...t, isDone: !t.isDone }
        }
        return { ...t }
      })
    },
    handleShowHidelist() {
      this.showList = !this.showList
    }
  }
}
</script>

<style>
  .line-through {
    text-decoration: line-through;
  }
  li{
    cursor: pointer;
  }
</style>
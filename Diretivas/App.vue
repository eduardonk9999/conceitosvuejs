<template>
  <div>
    <h1>Minha lista de tarefas!</h1>

    <ul>
      <li 
        v-for="(task, index) in tasks"
        :key="`${task}-${index}`"
      >
        {{ task.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: () => ({
    tasks: [
      { name: 'Fazer o curso', isDone: false}
    ]
  })
}
</script>

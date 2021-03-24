<template>
  <div>
    <h1>Minha lista de tarefas!</h1>

    <ul>
      <li 
        v-for="task in tasks"
        :key="`${task}-${index}`"
      >
        {{ tasks.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data: () => ({
    tasks: [
      { name: 'Fazer o curso', isDone: False}
    ]
  })
}
</script>

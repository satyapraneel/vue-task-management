<template>
    <div :class="[task.reminder ? 'reminder': '', 'task']" @dblclick="$emit('toggle-reminder', task.id)">
        <h3>{{ task.text }} 
          <i class="fa-regular fa-trash-can" @click="onDelete(task.id)"></i>
        </h3>
        <p>{{ task.day }}</p>
    </div>
</template>

<script>
    export default {
        name: "Task",
        props: {
            task: Object,
        },
        methods: {
          onDelete(id) {
            this.$emit('delete-task', id)
          }
        },
        // emits: ['toggle-reminder']
    }
</script>
<style scoped>
.fa-regular {
  color: red;
}
.task {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.task.reminder {
  border-left: 5px solid green;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
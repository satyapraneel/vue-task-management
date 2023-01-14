
<template>
   <AddTask v-show="showAddTask" @add-task="addNewTask"/>
   <Tasks :tasks="tasks" @delete-task="deleteTask" @toggle-reminder="toggleReminder"/>
</template>
<script>
import Tasks from '../components/Tasks.vue';
import AddTask from '../components/AddTask.vue';
export default {
  name: "HomeView",
  components: {
    Tasks,
    AddTask
  },
  data() {
    return {
      tasks: []
    }
  },
  props: {
    showAddTask: Boolean
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctor Appointment",
        day: "March 1st at 2:30 PM",
        reminder: true
      },
      {
        id: 2,
        text: "Meeting at school",
        day: "March 3rd at 2:30 PM",
        reminder: true
      },
      {
        id: 3,
        text: "Food Shopping",
        day: "March 4th at 2:30 PM",
        reminder: false
      },

    ]
  },
  methods: {
    deleteTask(id) {
      // if(confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      // }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
    },
    addNewTask(task) {
      this.tasks = [...this.tasks, task]
    },
  }

}
</script>
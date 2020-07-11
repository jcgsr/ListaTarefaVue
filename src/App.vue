<template>
  <div id="app">
    <h1>Lista de Tarefas Vue</h1>
    <TaskProgress :progress="progress" />
    <NewTask @taskAdded="addTask" />
    <TaskGrid :tasks="tasks" @taskDeleted="deleteTask" @taskStateChanged="toggleTaskState" />
    <p>{{ currentDate }}</p>
    <Footer />
  </div>
</template>

<script>
import TaskGrid from './components/TaskGrid.vue'
import Footer from './components/Footer.vue'
import TaskProgress from './components/TaskProgress.vue'
import NewTask from './components/NewTask.vue'

export default {
	components: { TaskGrid, NewTask, TaskProgress, Footer },
	data() {
		return {
			tasks: [],
      currentDate: ''
		}
	},
	computed: {
		progress() {
			const total = this.tasks.length
			const done = this.tasks.filter(t => !t.pending).length
			return Math.round(done / total * 100) || 0
		}
	},
	watch: {
		tasks: {
			handler() {
				localStorage.setItem('tasks', JSON.stringify(this.tasks))
			},
			deep: true,
		}
	},
	methods: {
		addTask(task) {
			const sameName = t => t.name === task.name
			const reallyNew = this.tasks.filter(sameName).length == 0
			if (reallyNew) {
				this.tasks.push({
					name: task.name,
					pending: task.pending || true
				})
			}
		},
		deleteTask(i) {
			this.tasks.splice(i, 1)
		},
		toggleTaskState(i) {
			this.tasks[i].pending = !this.tasks[i].pending
		},
    today() {
      let date = new Date()
      this.currentDate = date.toLocaleDateString('pt-BR', {
        day: '2-digit',
        month: 'short',
        year: 'numeric'
      })
    }
  },
		mounted() {
			const json = localStorage.getItem('tasks')
			const array = JSON.parse(json)
			this.tasks = Array.isArray(array) ? array : []
      this.today()
		}
	}

</script>

<style>
body {
  font-family: "Lato", sans-serif;
  /* background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115)); */
  background-color: rgba(241, 241, 194, 0.705);
}

h1 {
  padding: 2rem;  
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;  
}

#app h1 {
  margin-bottom: 5px;
  font-weight: 300;
  font-size: 3rem;
  font-weight: bold;
  color:#0a0455;
}

#app p {
	color: beige;
}
</style>

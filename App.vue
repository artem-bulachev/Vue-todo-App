<template>
  <v-app>
    <v-flex xs12 sm6 offset-sm3>
      <v-card>
        <v-card-title primary-title class="title">
          <div>
            <h3 class="mat-h2 mb-0">Todos</h3>
          </div>
        </v-card-title>
        <v-card-text>
          <TodoItem v-for="(todo, index) in todos"
                    :key="index"
                    :todo="todo">
          </TodoItem>
          <InputField ref="todoInput"></InputField>
        </v-card-text>
      </v-card>
    </v-flex>
  </v-app>
</template>

<script>
import TodoItem from './components/TodoItem'
import InputField from './components/InputField'

export default {
  name: 'App',
  components: {
    TodoItem,
    InputField
  },
  data () {
    return {
    }
  },
  computed: {
    todos () {
      return this.$store.state.todos
    }
  },
  methods: {
    addTodo () {
      this.$refs.todoInput.addTodo()
    }
  }
}
</script>

<style>
  .title {
    display: flex;
    justify-content: center;
  }
</style>

<template>
  <v-form>
    <v-text-field v-model="newItemTitle"
                  label="What do you need to do?"
                  @keydown.enter.prevent="addTodo"
                  autofocus
                  :rules="[rules.minLength]"
                  required
                  >
    </v-text-field>
  </v-form>
</template>

<script>
const MIN_LENGTH_VALIDATION = 1

export default {
  name: 'InputField',
  data () {
    return {
      newItemTitle: '',
      rules: {
        minLength: value => {
          return (value.length >= MIN_LENGTH_VALIDATION) || "It's empty"
        }
      }
    }
  },
  methods: {
    addTodo () {
      if (this.newItemTitle.length >= MIN_LENGTH_VALIDATION) {
        this.$store.dispatch('addTodo', this.newItemTitle)
        this.newItemTitle = ''
      }
    }
  }
}
</script>

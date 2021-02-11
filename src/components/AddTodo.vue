<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo.." :class="[title.length < 2 ? 'red':'green']">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
export default {
    name: "AddTodo",
    data(){
        return {
            title:''
        }
    },
    methods: {
        addTodo(e){
            e.preventDefault();
            const newTodo = {
                title: this.title,
                completed: false
            }
            // Send up to parent
            this.$emit('add-todo', newTodo)
            
            this.title = ""
        }
    }
}
</script>

<style scoped>
  form {
    display: flex;
  }
  .red{
      border: 2px solid red
  }
    .green{
      border: 2px solid green
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }
</style>
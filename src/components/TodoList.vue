<!-- Actual Development page where we can develop our problem statement -->

<!-- VueJs Template -->
<template>
    <div>
        <!-- Heading Just after the logo provided in App.vue -->
        <h1>todos</h1>
        <h6>VueJS SINGLE PAGE APPLICATION</h6>

        <!-- Text Box to enter todos by user -->
        <input type="text" class='todoInsert' placeholder="Enter Your To Do Task" 
        v-model="newTodo" @keyup.enter="AddTodo">

        <!-- Prints all the todoes enter by the user along with a checkbox -->
        <div v-for="(todo, index) in todos" :key="todo.id" class="todoItem">
            <div class="todo-item-label" :class="{ completed : todo.completed}">
                <input type="checkbox" v-model="todo.completed">  {{todo.title}} 
            </div>

            <!-- Cross button to remove todo from list -->
            <div class='todoRemove' @click="RemoveTodo(index)">
                &times;<!-- HTML Entiety for Close button -->
            </div>
        </div>
    
        <!-- Footer that contains a checkbox to check all the task in a single click 
         & another section that shows no of active todos  -->
        <div class="footerContainer">
            <div> 
                <label>
                    <input type="checkbox" :checked="!AnyTodoRemaining" @change="CheckAllTodo"> Check All
                </label> 
            </div>
      
            <div>
                {{ Remaining }} items left
            </div>  
        </div>
    </div>
</template>

<!-- Scripting part that contains programming functionalities -->
<script>
    export default {
        /* This name is used to refrence it as a tag in App.vue*/
        name: 'todo-list',
    
        /* The Data function contains the dummy Database for the todo app */
        data () {
            return {
               
                newTodo: '',     /*Empty todo */
                idForTodo: 1,    /*Id for the first object of todos container */
                todos: [],       /*Todo Container */
            }
        },

        /* Computed property used to describe functions and values that depends on other values */
        computed: {
            Remaining () {
                return this.todos.filter(todo => !todo.completed).length;
            },
            AnyTodoRemaining () {
                return this.Remaining != 0;
            }
    },

    /* Methods or Functions */
    methods: {
        /*To Add new ToDo */
        AddTodo() {
            if(this.newTodo.trim() == 0){
                return; /*Check for Empty value and if there is emty value then return */
            }

            /* Enter todo */
            this.todos.push({
                id: this.idForTodo,
                title: this.newTodo,
                completed: false,
            })

            /* Set next to do object and increment id by 1 */
            this.newTodo = '';
            this.idForTodo++;
        },
        
        /* Splice method used to delete object from todos container */
        RemoveTodo(index){
            this.todos.splice(index, 1);
        },

        /* Check all todo in a single click */
        CheckAllTodo () {
            this.todos.forEach((todo) => todo.completed = event.target.checked)
        }
    },
}
</script>

<!-- Styling as Required -->
<style>
    .todoInsert {
        width: 60%;
        padding: 1% 2%;
        font-size: 100%;
        margin-bottom: 2.5%;
    }

    .todoItem {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding-bottom: 1%;
        padding-left: 22%;
        padding-right: 22%;
        text-align: left;
    }

    .todoRemove{
        cursor: pointer;
    }

    .completed {
        text-decoration: line-through;
        color: red;
    }

    .footerContainer{
        display: flex;
        align-items: center;
        justify-content: space-between;
        font-size: 100%;
        border-top: 2px solid #2c3e50; 
        padding-top: 1%;
        margin: 3% 20% 0% 20%;
        padding: 1% 2% 1% 2%;
        /*top right bottom left */
    }

    h1,h6{
        margin: 0px;
    }

    h6{
        margin-bottom: 35px;
    }
</style>

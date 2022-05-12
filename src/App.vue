<template>
  <div id="app">
    <div class="bg">
      <div class="todolist">
        <div class="list_box">
          <div class="title">
            <h1>{{title}}</h1>
          </div>
          <div class="add">
            <div class="input_box">
              <input id="input" v-model="input" placeholder="할 일을 입력하세요." />
            </div>
            <div class="add_button" v-on:click="addTodo" >
              <img src="./img/add.png" />
            </div>
          </div>
          <div class="body">
            <div class="todoView" v-for="item in todos" v-bind:key="item.id">
              <span>{{ item.content }}</span>
              <div class="modifyDelete">
                <div v-on:click="onOffToggle(item)" >
                  <img v-if="item.toggle===false" src="./img/pencil.png" />
                  <img v-else-if="item.toggle===true" src="./img/confirm.png" />
                </div>
                <div v-on:click="deleteTodo(item)" >
                  <img v-if="item.modify===false" src="./img/delete.png" />
                  <img v-else-if="item.modify===true?deleteTodo(item):console.log('hi')" />
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      input: '',
      title: "To Do List",
      todos: []
    };
  },
  methods: {
    addTodo() {
      console.log('hello')
      const todoElement = []
      console.log(this.todos)
      if(this.todos.length == 0){
        todoElement.id = 1
        console.log(todoElement.id)
      } else {
        todoElement.id = this.todos[this.todos.length-1].id +1
      }
      todoElement.content = this.input
      todoElement.toggle = false
      todoElement.modify = false
      if(input.value == '') {
        alert('칸이 비었습니다.')
      } else {
        this.todos.push(...[todoElement])
        this.input = ''
      }
    // },
    // onOffToggle(item) {
    //   console.log('눌려')
    //   const arr = [...this.todos]
    //   console.log('arr', arr)
    //   console.log('item.id', item.id)
    //   console.log('item', item)
    //   arr.map(x => (x.id === item.id) ? { ...x, toggle: !x.toggle } : { ...x })
    //   // this.todos.push(...[arr])
    //   console.log('arr', arr)
    //   this.todos.push(...[arr])
    //   console.log(this.todos)
    },
    deleteTodo(item) {
      console.log(this.todos)
      console.log(item, 'item입니다')
      console.log(item.id, 'item.id입니다')
      const arr = this.todos.filter(x => x.id!==item.id)
      this.todos = arr
      // console.log(arr)
      // this.todos.push(...[arr])
    }
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#app .bg {
  display: flex;
  justify-content: center;
}

.todolist {
  display: flex;
  justify-content: center;
  max-width: 700px;
}

.todolist .add {
  display: flex;
  margin : 20px;
  justify-content: center;
}

.todolist .list_box .body {
  margin: 20px;
}
.todolist .list_box .body .todoView span {
  font-weight: bold;
  font-size: 25px;
}

.todolist .list_box .body .todoView span::before {
  content: "■";
  color: #8b0e97;
  margin-right: 5px;
  font-size: 20px;
}
.todolist .list_box .body .todoView {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.todolist .list_box .body .todoView .modifyDelete {
  display: flex;
}

.add .input_box {
  border-bottom: solid 5px #5A5A5A;
  width: 430px;
  margin-right: 20px;
}

.add .input_box input {
  height: 100%;
  width: 100%;
  border-style: none;
  padding-left: 10px;
  font-size: 20px;
  outline: none;
  font-weight: bold;
}

.add_button img {
  width: 50px;
  height: 50px;
}

img {
  width: 50px;
  height: 50px;
}
</style>

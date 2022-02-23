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
              <input v-model="input" placeholder="할 일을 입력하세요." />
            </div>
            <div class="add_button" v-on:click="addTodo" >
              <img src="./img/add.png" />
            </div>
          </div>
          <div class="body">
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
      title: "To Do List",
      todo: {

      },
    };
  },
  methods: {
    addTodo() {
      console.log('hello')
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

.todolist .add {
  display: flex;
  margin : 20px;
  justify-content: center;
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
</style>

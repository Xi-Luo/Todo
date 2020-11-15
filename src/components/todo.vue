<template>
  <div>
    <section class="todoapp">
      <header class="header"><h1>todos</h1>
        <input autofocus="autofocus" autocomplete="off" placeholder="What needs to be done?" class="new-todo">
      </header>
      <section class="main">
      <input id="toggle-all" type="checkbox" class="toggle-all">
        <label for="toggle-all">Mark all as complete</label>
        <ul class="todo-list" v-for="item in list" v-bind:key="item.id">
          <li class="todo">
            <div class="view">
            <input type="checkbox" class="toggle">
              <label>{{item.name}}</label>
              <button class="destroy"></button>
            </div>
            <input type="text" class="edit">

          </li>
        </ul>
<!--        <ul class="todo-list">-->
<!--          <li class="todo">-->
<!--            <div class="view">-->
<!--            <input type="checkbox" class="toggle">-->
<!--            <label>aaa</label>-->
<!--            <button class="destroy"></button>-->
<!--            </div>-->
<!--            <input type="text" class="edit">-->
<!--          </li>-->
<!--          <li class="todo completed">-->
<!--            <div class="view">-->
<!--              <input type="checkbox" class="toggle">-->
<!--              <label>dd</label>-->
<!--              <button class="destroy"></button>-->
<!--            </div>-->
<!--            <input type="text" class="edit">-->
<!--          </li>-->
<!--        </ul>-->
      </section>
      <footer class="footer"><span class="todo-count">
        <strong>1</strong> item left
				</span> <ul class="filters">
      <li><a href="#/all" class="selected">All</a></li>
      <li><a href="#/active" class="">Active</a></li>
      <li><a href="#/completed" class="">Completed</a></li>
    </ul>
      <button class="clear-completed" @click="clearComplete">
      Clear completed
      </button>
      </footer>
    </section>
    <footer class="info">
      <p>Double-click to edit a todo</p>
      <p>Written by <a href="http://evanyou.me">Evan You</a></p>
      <p>Part of <a href="http://todomvc.com">TodoMVC</a></p>
    </footer>
  </div>
</template>
<script>

export default {
name: "todo",
  data(){
    return {
      itemLeft:'',
      name:'',
      content:{
        id:'',
        name:''
      },
      list:[
        {
          id: 1,
          name:'aaa',
          done:true},
        {
          id:2,
          name: 'bbb',
          done:false
        }
      ]
    }
  },
  methods:{

    newItem() {


    },
    clearComplete(){
      for(let i =0;i<this.list.length;i++){
        if(this.list[i].done===true){
          this.list.splice(i,1);
        }
      }
    }

  },
  computed:{

  }
}
</script>

<style lang="css">
@import "../assets/base.css";
@import "../assets/index.css";
</style>
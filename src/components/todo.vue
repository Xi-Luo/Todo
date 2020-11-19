<template>
  <div>
    <section class="todoapp">
      <header class="header"><h1>todos</h1>
        <input autofocus="autofocus" autocomplete="off"
               placeholder="What needs to be done?"
               class="new-todo" @keyup.enter="newItem" v-model="newOne">
      </header>
      <section class="main">
      <input id="toggle-all" type="checkbox" class="toggle-all">
        <label for="toggle-all">Mark all as complete</label>
        <ul class="todo-list" v-for="(item, index) in list" v-bind:key="index">
          <li class="todo">
            <div class="view">
            <input type="checkbox" class="toggle">
              <label>{{item.name}}</label>
              <button class="destroy" @click="deleteOne(index)"></button>
            </div>
            <input type="text" class="edit">

          </li>
        </ul>
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
      newOne:'',
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
      console.log('here is newitem')
      let l = {
        id: this.list.length,
        name: this.newOne,
        done:false
      }
      this.list.push(l);
    },
    deleteOne(index){
      this.list.splice(index,1)
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
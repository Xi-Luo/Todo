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
        <label for="toggle-all" @click="allChange">Mark all as complete</label>
        <ul class="todo-list" v-for="(item, index) in showList" v-bind:key="index">
          <li class="todo">
            <div class="view">
            <input type="checkbox" class="toggle" v-model="item.done">
              <label @dblclick="editItem(item)">{{item.name}}</label>
              <button class="destroy" @click="deleteOne(index)"></button>
            </div>
            <input type="text" class="edit">

          </li>
        </ul>
      </section>
      <footer class="footer"><span class="todo-count">
        <span v-if="quantity==1"><strong>1</strong> item left</span>
        <span v-if="quantity!=1"><strong>{{quantity}}</strong> items left</span>
				</span> <ul class="filters">
      <li><a href="#/all" :class="{selected:choice===1}" @click="all(1)">All</a></li>
      <li><a href="#/active"  :class="{selected:choice===2}" @click="active(2)">Active</a></li>
      <li><a href="#/completed" :class="{selected:choice===3}" @click="completed(3)">Completed</a></li>
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
      quantity:'',
      choice:1,
      newOne:'',
      showList:[],
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
  created() {
    this.showList = this.list;
    this.quantity = this.list.filter(function (li){return !li.done}).length
  },
  watch:{
  list(){console.log('watch',this.list)},
  showList(){console.log('watch',this.showList)},
  choice(){console.log('watch',this.choice)}
  },
  methods:{

    newItem() {
      let l = {
        id: this.list.length,
        name: this.newOne,
        done:false
      }
      this.list.push(l);
      this.showList = this.list.filter(function (li){return !(li.done)})
      this.newOne = '';
      this.quantity = this.list.filter(function (li){return !(li.done)}).length;
    },
    allChange(){
      let count=0;
      for(let i = 0;i<this.list.length;i++){
        if(this.list[i].done===false){
          count ++;
          this.list[i].done = true;
        }
      }
      if(count===0){
        for(let i = 0;i<this.list.length;i++){
          this.list[i].done = false;

        }
      }
    },
    // check(index){
    //
    // },
    all(index){
      this.choice = index;
      this.showList = this.list.filter(function (li){return li})
    },
    active(index){
      this.choice = index;
      this.showList = this.list.filter(function (li){return !(li.done)})
    },
    completed(index){
      this.choice = index;
      this.showList = this.list.filter(function (li){return li.done})
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
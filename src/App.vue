<template>
  <div id="app">
    <Tab
      @chang_input_flag = "changeInputFlag"
    ></Tab>
    <Del :maskflag = "maskflag"
      :change_mask_flag_del = "changeMaskFlagDel"
      :del_index = "active_index"
      @close_mask = "closeMask"
      :remove = "remove"
    />
    <Container 
      :todos = " newTodos "
      :maskflag= " maskflag "
      @change_fished = "changeBtn"
      @remove_todos = "check"
      @close_mask = "closeMask"
      :input_flag = "input_flag"
      @closeInput = "closeInput"
      @add_todos = "addTodos"
    ></Container>
    <tab-bar
      :type = " type "
       @get_type="changeType"
    ></tab-bar>
  </div>
</template>

<script>
import Container from './components/Container.vue'
import Tab from './components/Tab.vue'
import TabBar from './components/TabBar.vue'
import Del from './components/Del.vue'

export default {
    name: 'app',
    components: {
      Container,
      Tab,
      TabBar,
      Del
    },
    data(){
      return{
        type:'A',
        done:false,
        input_flag:false,
        maskflag:false,
        active_index:0,
        todos:[{
            id:1,
            title:" zhanghuiqi's todolist ",
            task:'等风来不如追风去',
            done:false
        },
        {
            id:2,
            title:" zhanghuiqi's todolist ",
            task:'我是大雪纷飞里自在漂浮的人啊',
            done:true
        }
        ]
    }
    
  },
  methods:{
    changeBtn(index){
        this.todos[index].done = !this.todos[index].done
    },
    closeMask(){
        this.maskflag = false
    },
    closeInput(){
      this.input_flag = false
    },
    check(index){
      const flag = this.todos[ index ].done;

      if(flag){
        this.remove(index)
      }else{
        this.active_index = index
        console.log( this.active_index)
        this.changeMaskFlagDel()
      }

    },
    remove( index ){
      this.todos.splice(index,1)
    },
    changeMaskFlagDel(){
      this.maskflag = true
    },
    addTodos( val){
      this.todos.push({
          id:sort( this.todos )[ 0 ].id + 1,
          task:val,
          done:false
        })
        this.input_flag = false;

    },
    changeInputFlag(){
      this.input_flag = true
    },
    changeType( val ){
      this.type = val
    }
  },
   computed: {
     newTodos(){
       switch( this.type ){
         case 'A':
           return this.todos;
           break;
          case 'F':
            return this.todos.filter( item=>item.done );
            break;
          case 'U':
            return this.todos.filter( item=>!item.done );
            break;
       }
     }
   }

  }
  function sort( arr ){
  return arr.sort(function( a,b ){
    return b.id - a.id;
  })
}
</script>

<style lang="stylus">
#app
  font-family 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  margin-top 60px
</style>

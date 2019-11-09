<template id="container">
    <div class="content">
            <div class="mask-box"  v-if = "input_flag">
                <div class="bg" @click = "closeInput" ></div>
                <div class="mask-content">
                <textarea name="" id="" cols="" rows="" width="100%"
                @keyup.enter = "addTodos"
                ></textarea>
                <button class="button btn2 button-round button-fill pull-center" 
                
                > enter </button>
                </div>
            </div>
        <div class="card" 
            v-for = "( item,index) in todos"
            :key = "item.id"
        >
            <div class="card-header">
                {{ item.title }}
            </div>
            <div class="card-content">
            <div class="card-content-inner content">{{ item.task }}</div>
            </div>
            <div class="myfooter pull-right"> 
                <button class="button button-success"  
                  :class = "{ 'button-fill':item.done  }"
                  @click = "changeDone( index )"
                 >
                    <span class="icon icon-check"></span>
                </button>
                    <button href="#" class="button button-danger "
                        @click = "remove_todos(index)"
                    >
                    <span class="icon icon-remove"></span>
                </button>
                </div>
            
        </div>
    </div>
</template>


<script>

export default {
   
    props:['todos',"maskflag","input_flag"],
    methods:{
        changeDone(index){
            this.$emit('change_fished',index);
        },
        remove_todos( index ){
            this.$emit('remove_todos',index)
        },
        closeInput(){
            this.$emit('closeInput') 
        },
        addTodos(e){
            this.$emit('add_todos', e.target.value)

        }
    },
}
</script>
<style lang="stylus">
    .content
        text-align left
    
</style>
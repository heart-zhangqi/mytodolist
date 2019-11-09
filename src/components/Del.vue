<template id="mask" >
        <div class="mask-box" v-if = "maskflag" >
            <div class="bg"  @click.self = "closeMask"></div>
            <div class="mask-content">
            <p> 待办事项还未完成，确定要删除吗？ </p>
            <button class="button button-danger button-fill pull-right" 
                @click= "corfim"
            > OK </button>
            </div>
        </div>
    </template>

<script>
export default {
    props:["maskflag","del_index","remove"],
    methods:{
        closeMask(){
            this.$emit('close_mask')
        },
        corfim(){
            this.closeMask()
            this.remove()
        }
    }
}
</script>
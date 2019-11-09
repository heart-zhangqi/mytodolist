 <template id="tab">
    <header class="bar bar-nav">
        <a class="icon icon-left pull-left"></a>
        <a class="icon icon-edit pull-right" 
            @click = "changInput"
        ></a>
        <h1 class="title">
            zhanghuiqi's todolist
        </h1>
    </header>
</template>

<script>
export default {
   methods: {
       changInput(){
           this.$emit('chang_input_flag')
       }
   },
    
    
}
</script>
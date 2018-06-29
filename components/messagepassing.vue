<template>
    <div >
        <input v-model="message"><button @click="sendMessage">Send message</button>

    </div>
</template>
<script>
    export default{
        methods:{
            sendMessage(){
                this.$emit('send-message',this.message);
            }
        },
        data (){
            return {
                message:''
            }
        }

    }
</script>
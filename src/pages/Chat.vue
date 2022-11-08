<template>
  
</template>

<script>
export default {
    mounted(){
        let ws = new WebSocket('ws://localhost:8080');
        // Connection opened
        ws.addEventListener('open', (event) => {
            ws.send('Hello Server!');
        });
        // Listen for messages
        ws.addEventListener('message', (event) => {
            console.log('Message from server ', event.data);
        });
    }
}
</script>

<style>
</style>
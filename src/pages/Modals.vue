<template> 
<img-modal v-show="active" @close="active=false" src="http://placekitten.com/800/600"></img-modal>
<button class="button is-white" @click="active=true">Open Modal</button>
<img-modal v-show="active2" @close="active2=false" src="https://placebear.com/800/600"></img-modal>
<button class="button is-white" @click="active2=true">Open Modal2</button>
<modal v-show="active3" @close="active3=false">
    <h1>TANN PANN ROOSTE VANN</h1>
</modal>
<button class="button is-white" @click="active3=true">Open Modal3</button>
  
</template>

<script>
import ImgModal from '../components/ImgModal.vue'
import Modal from '../components/Modal.vue'
export default {
    components: { Modal, ImgModal },
    data(){
        return {
            active: false,
            active2: false,
            active3: false
        }
    }

}
</script>

<style>

</style>
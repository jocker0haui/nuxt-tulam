<template>
    <div class="grid wide">
      <div class="row">
        <div class="c3">
          <button @click="onOpenModal('modalcard')"  style="margin-top:200px">modal</button>
          <button @click="onOpenModal('modalcard')"  style="margin-top:200px">modal</button>
          <button @click="onOpenModal('modalcard')"  style="margin-top:200px">modal</button>
        </div>
      </div>
      <v-modal name="modalcard">
        <div class="modalcard-body">
          <h1>Create a new card</h1>
          <button @click="onCloseModal">close</button>
        </div>
      </v-modal>
    </div>
</template>

<script>
export default {
  name: 'IndexPage',
  methods : {
    onOpenModal(name){
      console.log(name)
      switch (name) {
        case 'modalcard':
          this.$modal.open({name:'modalcard'})
          break;
      
        default:
          break;
      }
    },
    onCloseModal(){
      this.$modal.close({name : 'modalcard'})
    }
  }
}
</script>

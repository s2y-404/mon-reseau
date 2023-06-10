
<template>
  <div class="card card-items">
    <img :src="require(`@/assets/${this.data.image}.png`)" class="card-img-top" alt="Photo de profil" />
    <div class="card-body">
      <span class="card-title fw-bold">{{ data.name }}</span>
    </div>
    <i class="btn fa-solid fa-xmark mx-2" data-bs-toggle="modal" :data-bs-target="`#deleteModal${data.id}`"></i>
  </div>

  <!-- Modal -->
  <div class="modal fade" :id="`deleteModal${data.id}`" tabindex="-1" aria-labelledby="deleteModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h1 class="modal-title fs-5" id="deleteModalLabel">Modal title</h1>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <i class="fa-solid fa-question"></i> <span>Etes-vous sûr de vouloir supprimer {{ data.name }} de votre réseau ?</span>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Cancel</button>
          <button type="button" class="btn btn-primary" data-bs-dismiss="modal" @click="removeCard()">OK</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardComponent',
  props: {
    data: Object
  },
  emits: ['remove'],
  methods: {
    removeCard() {
      this.$emit('remove')
      console.log(`Card     | ${this.data.id}`)
    },
  }
};
</script>

<style scoped>
  img {
    width: 80px;
  }

  .modal i {
    margin-right: 15px;
    padding: 12px 15px;
    border: 2px solid #2c3e50;
    border-radius: 100%;
  }

  .card-items {    
    width: 18.2em; 
    height: 80px; 
    
    display: flex; 
    flex-direction: row;
    align-items: center;
    flex: 1 0 500px;
    box-sizing: border-box;
    margin: 1rem .25em;
  }
</style>

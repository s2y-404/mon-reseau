
<template>
  <div class="card d-flex flex-row align-items-center px-2" style="width: 18rem; height: 80px;">
    <img :src="image" class="card-img-top" alt="Photo de profil" />
    <div class="card-body">
      <span class="card-title fw-bold">{{ name }}</span>
    </div>
    <i class="btn fa-solid fa-xmark mx-2"></i>
  </div>
</template>

<script>
export default {
  name: 'CardComponent',
  props: {
    id: Number,
    name: String,
    profile_picture: String,
    type: String
  },
  computed: {
    image() {
      return require(`@/assets/${this.profile_picture}.png`);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .card {
    margin: 3% 0;
  }

  img {
    width: 80px;
  }

</style>

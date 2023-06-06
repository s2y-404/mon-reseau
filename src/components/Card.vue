
<template>
  <div class="card d-flex flex-row align-items-center px-2" style="width: 18rem; height: 80px;">
    <img :src="require(`@/assets/${this.data.image}.png`)" class="card-img-top" alt="Photo de profil" />
    <div class="card-body">
      <span class="card-title fw-bold">{{ data.name }}</span>
    </div>
    <i class="btn fa-solid fa-xmark mx-2" @click="removeCard()"></i>
  </div>
</template>

<script>
export default {
  name: 'CardComponent',
  props: {
    data: Object
  },
  methods: {
    removeCard() {
      this.$emit('remove')
    },
  }
};
</script>

<style scoped>
  .card {
    margin: 3% 0;
  }

  img {
    width: 80px;
  }

</style>

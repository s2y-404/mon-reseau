
<template>
    <div class="card-list">
      <div v-for="data in this.datas" :key="data.id">
        <CardComponent :id="data.id" :name="data.name" :profile_picture="data.image" :type="data.type" />
      </div>
    </div>
</template>

<script>
import CardComponent from '@/components/Card.vue';

export default {
  components: {
    CardComponent
  },
  props: {
    datas: Array
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .card-list {
    display: grid;
    grid-template-columns: repeat(auto-fill,minmax(18rem, 1fr));
    justify-items: center;
  }

</style>

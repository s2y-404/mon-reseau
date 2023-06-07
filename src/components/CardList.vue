
<template>
    <div v-if="this.dataList.length === 0" class="d-flex justify-content-center align-items-center">
      <img src="@/assets/users_blank.png" alt="Répertoire vide" style="width: 45%;">
    </div>
    <div v-else class="card-list">
      <div v-for="data in this.dataList" :key="data.id">
        <CardComponent  
          :data="data" 
          @remove="() => removeCard(data.id)" 
        />
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
    dataList: Array
  },
  emits: ['remove', 'datas-updated', 'datasUpdated'],
  data() {
    return {
      localDataList: [...this.dataList]
    };
  },
  methods: {
    removeCard(id) {
      console.log("Removing card with id:", id);
      this.localDataList = this.localDataList.filter(item => item.id !== id);
      this.$emit('remove', id);
    }
  }
};
</script>

<style scoped>
  .card-list {
    display: grid;
    grid-template-columns: repeat(auto-fill,minmax(18rem, 1fr));
    justify-items: center;
  }

</style>

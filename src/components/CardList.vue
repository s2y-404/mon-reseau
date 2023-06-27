
<template>
    <div v-if="!this.dataList.length || !this.arrayFilter.length" class="d-flex justify-content-center align-items-center">
      <img src="@/assets/users_blank.png" alt="Répertoire vide" style="width: 45%;">
    </div>
    <div v-else-if="this.dataList.length || this.arrayFilter.length" class="card-list">
      <div v-for="data in this.dataList.filter(element => element.name.match(new RegExp(`${this.searchFilter}`, 'ig')))" :key="data.id">
        <CardComponent  
          v-if="this.arrayFilter.includes(data.type)"
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
    dataList: Array,
    arrayFilter: Array,
    searchFilter: String
  },
  emits: ['remove', 'datas-updated', 'datasUpdated'],
  data() {
    return {
      localDataList: [...this.dataList]
    };
  },
  methods: {
    removeCard(id) {
      console.log("CardList | Removing card with id:", id);

      this.localDataList = this.localDataList.filter(item => item.id !== id);
      this.$emit('remove', id);
    }
  }
};
</script>

<style scoped>
  .card-list {
    display: flex;
    flex-wrap: wrap;
  }

</style>

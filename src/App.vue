<template>
  <HeaderComponent />
  <NavbarComponent nbInvitation="6" :datas="dataList" @datas-updated="handleDatasUpdated" />
  <FilterComponent />
  <CardListComponent :dataList="dataList" @remove="handleDatasDeleted" />
</template>

<script>
import HeaderComponent from './components/Header.vue';
import NavbarComponent from './components/Navbar.vue';
import FilterComponent from './components/Filter.vue';
import CardListComponent from './components/CardList.vue';

export default {
  name: 'App',
  components: {
    HeaderComponent,
    NavbarComponent,
    FilterComponent,
    CardListComponent,
  },
  methods: {
    handleDatasUpdated(newDatas) {
      this.dataList = newDatas;
    },
    handleDatasDeleted(id) {
      console.log("Card removed");
      this.dataList = this.dataList.filter(item => item.id !== id);
    }
  },
  data() {
    return {
      "dataList": [
        {
          "id": "0",
          "name": "Doe John",
          "type": "user",
          "image": "pp_m_2"
        },
        {
          "id": "1",
          "name": "Smith Emma",
          "type": "user",
          "image": "pp_w_1"
        },
        {
          "id": "2",
          "name": "Johnson Michael",
          "type": "user",
          "image": "pp_m_2"
        },
        {
          "id": "3",
          "name": "Williams Olivia",
          "type": "user",
          "image": "pp_w_1"
        },
        {
          "id": "4",
          "name": "Brown James",
          "type": "user",
          "image": "pp_m_1"
        },
        {
          "id": "5",
          "name": "Jones Sophia",
          "type": "user",
          "image": "pp_w_1"
        },
        {
          "id": "6",
          "name": "Davis Daniel",
          "type": "user",
          "image": "pp_m_2"
        },
        {
          "id": "7",
          "name": "Miller Isabella",
          "type": "user",
          "image": "pp_w_2"
        },
        {
          "id": "8",
          "name": "Dailybiz Dragon",
          "type": "group",
          "image": "pp_g"
        }
      ]
    };
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  color: #2c3e50;

  padding: 0 10%;
}
</style>

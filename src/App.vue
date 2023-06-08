<template>
  <HeaderComponent />
  <NavbarComponent nbInvitation="6" :datas="dataList" @datas-updated="handleDatasUpdated" />
  <FilterComponent @filter-checked-updated="handleFilterCheckedUpdated" />
  <CardListComponent :dataList="dataList" :arrayFilter="arrayFilter" @remove="handleDatasDeleted" />
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
      console.log(newDatas)
      this.dataList = newDatas;
      this.$emit('datas-updated', newDatas)
    },
    handleDatasDeleted(id) {
      console.log("App | Card removed");
      this.dataList = this.dataList.filter(item => item.id !== id);
      this.$emit('datasUpdated');
    },
    handleFilterCheckedUpdated(filterChecked) {
      this.arrayFilter = filterChecked
    }
  },
  data() {
    return {
      "dataList": [
        {
          "id": "0",
          "name": "Doe John",
          "type": "friend",
          "image": "pp_m_2"
        },
        {
          "id": "1",
          "name": "Smith Emma",
          "type": "friend",
          "image": "pp_w_1"
        },
        {
          "id": "2",
          "name": "Johnson Michael",
          "type": "friend",
          "image": "pp_m_2"
        },
        {
          "id": "3",
          "name": "Williams Olivia",
          "type": "friend",
          "image": "pp_w_1"
        },
        {
          "id": "4",
          "name": "Monkey 🦧",
          "type": "admin",
          "image": "pp_a"
        },
        {
          "id": "5",
          "name": "Jones Sophia",
          "type": "friend",
          "image": "pp_w_1"
        },
        {
          "id": "6",
          "name": "NFL 🏈",
          "type": "admin",
          "image": "pp_a"
        },
        {
          "id": "7",
          "name": "NBA 🏀",
          "type": "group",
          "image": "pp_g"
        },
        {
          "id": "8",
          "name": "Dailybiz Dragon",
          "type": "group",
          "image": "pp_g"
        },
        {
          "id": "9",
          "name": "Brown James",
          "type": "friend",
          "image": "pp_m_1"
        }
      ],
      arrayFilter: ["friend", "group", "admin"]
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

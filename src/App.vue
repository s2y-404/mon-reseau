<template>
  <HeaderComponent />
  <NavbarComponent nbInvitation="6" :dataList="dataList" :searchData="searchData"  @dataListUpdated="handleDatasUpdated" />
  <FilterComponent @filter-checked-updated="handleFilterCheckedUpdated" @searchFilter-updated="handleSearchFilterUpdated" />
  <CardListComponent :dataList="dataList" :arrayFilter="arrayFilter" :searchFilter="searchFilter" @remove="handleDatasDeleted" />
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
      this.$emit('dataList-updated', newDatas)
    },
    handleDatasDeleted(id) {
      console.log(`App      | Card removed`)

      this.dataList = this.dataList.filter(item => item.id !== id);
      this.$emit('dataListUpdated');
    },
    handleFilterCheckedUpdated(filterChecked) {
      this.arrayFilter = filterChecked
    },
    handleSearchFilterUpdated(searchFilter) {
      this.searchFilter = searchFilter
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
          "name": "[SPORT] NFL 🏈",
          "type": "admin",
          "image": "pp_a"
        },
        {
          "id": "7",
          "name": "[SPORT] NBA 🏀",
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
      "searchData": [
        {
          "id": "10",
          "name": "[SPORT] FFF ⚽",
          "type": "group",
          "image": "pp_g"
        },
        {
          "id": "11",
          "name": "Anderson David",
          "type": "friend",
          "image": "pp_m_2"
        },
        {
          "id": "12",
          "name": "les Warriors 🔥",
          "type": "group",
          "image": "pp_g"
        },
        {
          "id": "13",
          "name": "🥰 Les Besties 🥰",
          "type": "group",
          "image": "pp_g"
        },
        {
          "id": "14",
          "name": "Harris Emily",
          "type": "friend",
          "image": "pp_w_1"
        },
        {
          "id": "15",
          "name": "Jean-Pierre Matthew",
          "type": "friend",
          "image": "pp_m_2"
        },
        {
          "id": "16",
          "name": "Moore Jessica",
          "type": "friend",
          "image": "pp_w_2"
        },
        {
          "id": "17",
          "name": "Elon Musk",
          "type": "friend",
          "image": "elon"
        },
        {
          "id": "18",
          "name": "Moore Olivia",
          "type": "friend",
          "image": "pp_w_1"
        },
        {
          "id": "19",
          "name": "Miller Ethan",
          "type": "friend",
          "image": "pp_m_2"
        },
        {
          "id": "20",
          "name": "[SPORT] FFA 🏃‍♂️",
          "type": "group",
          "image": "pp_g"
        },
        {
          "id": "21",
          "name": "Leclerc Marie",
          "type": "friend",
          "image": "pp_w_2"
        },
        {
          "id": "22",
          "name": "Martin Sophie",
          "type": "friend",
          "image": "pp_w_2"
        },
        {
          "id": "23",
          "name": "Dubois Thomas",
          "type": "friend",
          "image": "pp_m_1"
        },
        {
          "id": "24",
          "name": "Moreau Camille",
          "type": "friend",
          "image": "pp_w_2"
        },
        {
          "id": "25",
          "name": "Lefebvre Laura",
          "type": "friend",
          "image": "pp_w_2"
        },
        {
          "id": "26",
          "name": "Roux Alexandre",
          "type": "friend",
          "image": "pp_m_1"
        },
        {
          "id": "27",
          "name": "Girard Emilie",
          "type": "friend",
          "image": "pp_w_2"
        },
        {
          "id": "28",
          "name": "Leroy Maxime",
          "type": "friend",
          "image": "pp_m_1"
        },
        {
          "id": "29",
          "name": "Fournier Julie",
          "type": "friend",
          "image": "pp_w_2"
        },
        {
          "id": "30",
          "name": "[SPORT] MLB ⚾",
          "type": "group",
          "image": "pp_g"
        },
        {
          "id": "31",
          "name": "Dupont Pierre",
          "type": "friend",
          "image": "pp_m_1"
        },
        {
          "id": "21",
          "name": "Morin Elodie",
          "type": "friend",
          "image": "pp_w_2"
        },
        {
          "id": "22",
          "name": "Dupont Antoine",
          "type": "friend",
          "image": "pp_m_1"
        },
        {
          "id": "23",
          "name": "Mercier Juliette",
          "type": "friend",
          "image": "pp_w_2"
        },
        {
          "id": "24",
          "name": "Lecomte Lucas",
          "type": "friend",
          "image": "pp_m_1"
        },
        {
          "id": "25",
          "name": "Leconte Mathilde",
          "type": "friend",
          "image": "pp_w_2"
        },
        {
          "id": "26",
          "name": "Dupuis Emilien",
          "type": "friend",
          "image": "pp_m_1"
        },
        {
          "id": "27",
          "name": "Marchand Charlotte",
          "type": "friend",
          "image": "pp_w_2"
        },
        {
          "id": "28",
          "name": "Dupuis Etienne",
          "type": "friend",
          "image": "pp_m_1"
        },
        {
          "id": "29",
          "name": "Lecomte Clara",
          "type": "friend",
          "image": "pp_w_2"
        }
      ],
      arrayFilter: ["friend", "group", "admin"],
      searchFilter: ''
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

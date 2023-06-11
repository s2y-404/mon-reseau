<template>
<div style="width: 445px;">
  <!-- input text -->
  <div class="input-group flex-nowrap" @input="onChangeInput">
    <span class="input-group-text" id="filter-search"><i class="fa-solid fa-magnifying-glass"></i></span>
    <input type="text" class="form-control" v-model="searchInput" placeholder="pseudo ou nom" aria-label="Username" aria-describedby="filter-search">
  </div>
  <!-- user/group add -->
  <div v-if="this.searchAdd.length > 0" class="searchAdd-group">
    <div v-for="element in this.searchAdd" class="searchAdd" :key="element.id">
      <img :src="require(`@/assets/${element.image}.png`)" class="card-img-top" alt="Photo de profil" />
      <span class="name flex-grow-1">{{ element.name }}</span>
      <i class="btn fa-solid fa-xmark text-end" @click="onDeleteSuggestion(element.id)"></i>
    </div>
  </div>
  <!-- suggestion -->
  <div v-if="this.searchInput.length >= 3" class="suggestion-group">
    <div v-for="data in this.localDatas" class="suggestion" :key="data.id" @click="onAddSuggestion(data)">
      <img :src="require(`@/assets/${data.image}.png`)" class="card-img-top" alt="Photo de profil" />
      <span class="name flex-grow-1">{{ data.name }}</span>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'SearchSuggestionComponent',
  props: {
    searchData: Array
  },
  data() {
    return {
      searchInput: '',
      localDatas: null,
      searchAdd: []
    }
  },
  methods: {
    onChangeInput() {
      this.localDatas = this.searchData.slice()
      var regex = new RegExp(`${this.searchInput}`, "ig")
      var arrayTemp = this.localDatas.filter(element => element.name.match(regex))

      this.localDatas = arrayTemp.slice(0, 3)
    },
    onAddSuggestion(data) {
      if (this.searchAdd.length < 5 && this.searchAdd.findIndex(el => el.id == data.id) === -1) {
        this.searchAdd.push(data)
      }
    },
    onDeleteSuggestion(id) {
      let indexDel = this.searchAdd.findIndex(el => el.id === id)
      this.searchAdd.splice(indexDel, 1)
    }
  },
  emits: []
}
</script>

<style scoped>
  .suggestion {
    width: 100%;
    height: 45px;
    background: #595959;
    color: #fff;
    border-bottom: .5px solid #000;
    display: flex;
    align-items: center;
    cursor: pointer;

  }
  .suggestion-group {
    width: 100%;
    height: var(45px * 3);
    border: 2px solid red;
  }
  img {
    width: 40px;
    height: 45px;
    object-fit: cover;
  }
  .name {
    padding: 0 4%;
  }

  .searchAdd-group {
    width: 100%;
    min-height: 45px;
    background: green;
    display: flex;
    justify-content: space-evenly;
    flex-wrap: wrap;
  }
  .searchAdd {
    width: 49%;
    height: 35px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: #969696;
    border-radius: 5px;
    overflow: hidden;
    margin: .5% 0;
    font-size: small;
  }
</style>

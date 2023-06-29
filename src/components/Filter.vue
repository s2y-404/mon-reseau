<template>
  <div id="filter" class="d-flex">
    <div class="flex-grow-1 d-flex">
      <div id="group-filtre" class="form-check me-5">
        <input class="form-check-input" type="checkbox" v-model="friend" @change="onCheck('friend')" id="myfriend" />
        <label class="form-check-label" for="myfriend">Mes amis</label>
      </div>
      <div id="group-filtre" class="form-check me-5">
        <input class="form-check-input" type="checkbox" v-model="group" @change="onCheck('group')" id="mygroup" />
        <label class="form-check-label" for="mygroup">Mes groupes</label>
      </div>
      <div id="group-filtre" class="form-check me-5">
        <input class="form-check-input" type="checkbox" v-model="admin" @change="onCheck('admin')" id="admin" />
        <label class="form-check-label" for="admin">Mes groupes admin</label>
      </div>
    </div>
    <div class="input-group flex-nowrap position-relative" @input="onChangeInput">
      <span class="input-group-text" id="filter-search"><i class="fa-solid fa-magnifying-glass"></i></span>
      <input type="search" class="form-control" placeholder="pseudo ou nom" v-model="search" aria-label="Username" aria-describedby="filter-search" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'FilterComponent',
  props: {
    dataList: Array
  },
  data() {
    return {
      filterChecked: ["friend", "group", "admin"],
      friend: true,
      group: true,
      admin: true,
      search: '',
    }
  },
  methods: {
    onCheck(checkbox) {
      (checkbox === "friend") && this.toggleArrayItem(this.filterChecked, "friend");
      (checkbox === "group")  && this.toggleArrayItem(this.filterChecked, "group");
      (checkbox === "admin")  && this.toggleArrayItem(this.filterChecked, "admin");

      this.$emit('filter-checked-updated', this.filterChecked);
    },
    toggleArrayItem(a, v) {
      var i = a.indexOf(v);
      if (i === -1)
        a.push(v);
      else
        a.splice(i, 1);
    },
    onChangeInput() {
      this.$emit('searchFilter-updated', this.search);
    },
  },
  emits: ['filter-checked-updated', 'searchFilter-updated']
}
</script>

<style scoped>
#filter {
  width: 100%;
  height: 50px;

  display: flex;
  justify-content: space-between;
  align-items: center;
}

.input-group {
  width: 300px;
}

</style>

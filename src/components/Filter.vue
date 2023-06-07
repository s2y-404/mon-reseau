<template>
  <div id="filter" class="d-flex">
    <div class="flex-grow-1 d-flex">
      <div id="group-filtre" class="form-check me-5">
        <input class="form-check-input" type="checkbox" id="friend" name="friend" checked />
        <label class="form-check-label" for="friend">Mes amis</label>
      </div>
      <div id="group-filtre" class="form-check me-5">
        <input class="form-check-input" type="checkbox" id="group" name="group" checked />
        <label class="form-check-label" for="group">Mes groupes</label>
      </div>
      <div id="group-filtre" class="form-check me-5">
        <input class="form-check-input" type="checkbox" id="admin" name="admin" checked />
        <label class="form-check-label" for="admin">Mes groupes admin</label>
      </div>
    </div>
    <div class="input-group flex-nowrap">
      <span class="input-group-text" id="filter-search"><i class="fa-solid fa-magnifying-glass"></i></span>
      <input type="text" class="form-control" placeholder="pseudo ou nom" aria-label="Username" aria-describedby="filter-search">
    </div>
  </div>
</template>

<script>
export default {
  name: 'FilterComponent',
  props: {
    nbInvitation: Number
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#filter {
  width: 100%;
  height: 50px;
  background-color: orange;

  display: flex;
  justify-content: space-between;
  align-items: center;
}

.input-group {
  width: 300px;
}

</style>

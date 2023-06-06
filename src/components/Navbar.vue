<template>
  <nav>
    <div class="btn btn-secondary ms-5" data-bs-toggle="modal" data-bs-target="#addModal">ajouter ami / groupe</div>
    <div class="btn btn-secondary ms-5">{{ nbInvitation }} Invitations en attente</div>
  </nav>

  <div class="modal fade" id="addModal" tabindex="-1" aria-labelledby="addModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h1 class="modal-title fs-5" id="addModalLabel">Faire une demande d'ajout d'un ami ou d'un groupe</h1>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <form @submit.prevent="onSubmit" id="FormAdd" class="d-flex flex-column">
          <div class="modal-body" style="padding: 5%;">

            <div>
              <div id="group-filtre" class="form-check form-check-inline me-5">
                <input class="form-check-input" type="radio" name="type" v-model="typeInput" value="type" checked />
                <label class="form-check-label" for="user">ami</label>
              </div>
              <div id="group-filtre" class="form-check form-check-inline me-5">
                <input class="form-check-input" type="radio" name="type" v-model="typeInput" value="group" />
                <label class="form-check-label" for="group">groupe</label>
              </div>
            </div>

            <div class="input-group flex-nowrap" style="margin: 5% 0;">
              <span class="input-group-text" id="nameInput"><i class="fa-solid fa-magnifying-glass"></i></span>
              <input type="text" class="form-control" placeholder="pseudo ou nom de groupe" v-model="nameInput" />
            </div>

          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">annuler</button>
            <button type="submit" class="btn btn-secondary" data-bs-dismiss="modal">ajouter</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NavbarComponent',
  props: {
    nbInvitation: Number,
    datas: Array,
  },
  groupedProps: ['typeInput', 'nameInput'],
  methods: {
    onSubmit() {
      const newDatas = this.datas.slice();
      const id = newDatas.length;
      const type = this.typeInput
      const name = this.nameInput
      const img = this.typeInput === "group" ? "pp_g" : "pp_m_1";

      newDatas.push({
        id: id,
        name: name,
        type: type,
        image: img
      });

      this.$emit('datas-updated', newDatas);
    },
  }

}
</script>

<style scoped>
nav {
  width: 100%;
  height: 50px;
  background-color: red;

  display: flex;
  justify-content: end;
  align-items: center;
}
</style>

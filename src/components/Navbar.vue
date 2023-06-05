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
        <div class="modal-body" style="padding: 5%;">
          <form @submit="onSubmit()" id="FormAdd" class="flex-grow-1 d-flex">
            <div id="group-filtre" class="form-check me-5">
              <input class="form-check-input" type="checkbox" id="friend" name="friend" />
              <label class="form-check-label" for="friend">ami</label>
            </div>
            <div id="group-filtre" class="form-check me-5">
              <input class="form-check-input" type="checkbox" id="group" name="group" />
              <label class="form-check-label" for="group">groupe</label>
            </div>
          </form>
          <div class="input-group flex-nowrap" style="margin: 5% 0;">
            <span class="input-group-text" id="navbar-name"><i class="fa-solid fa-magnifying-glass"></i></span>
            <input type="text" class="form-control" placeholder="pseudo ou nom de groupe" aria-label="Username" aria-describedby="navbar-name">
          </div>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">annuler</button>
          <button type="submit" class="btn btn-secondary">ajouter</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NavbarComponent',
  props: {
    nbInvitation: Number
  },
  methods: {
    onSubmit() {
      console.log("form submitted");
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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

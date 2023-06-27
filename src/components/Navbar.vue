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

            <div class="d-flex flex-column justify-content-center align-items-center">
              <!-- CHOIX DU TYPE (FRIEND OU GROUP) -->
              <div class="d-flex justify-content-around" style="width: 100%; padding: 1% 20% 4% 20%;">
                <div id="group-filtre" class="form-check form-check-inline">
                  <input class="form-check-input" type="radio" name="type" id="friend" v-model="typeInput" value="friend" checked />
                  <label class="form-check-label" for="friend">ami</label>
                </div>
                <div id="group-filtre" class="form-check form-check-inline">
                  <input class="form-check-input" type="radio" name="type" id="group" v-model="typeInput" value="group" />
                  <label class="form-check-label" for="group">groupe</label>
                </div>
              </div>
            </div>

            <SearchSuggestionComponent :searchData="searchData" :typeInput="typeInput" @dataListAdded="handleDatasAdded" />

          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">annuler</button>
            <button type="submit" class="btn btn-secondary">ajouter</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import SearchSuggestionComponent from './SearchSuggestion.vue';

export default {
  name: 'NavbarComponent',
  components: {
    SearchSuggestionComponent
  },
  props: {
    nbInvitation: String,
    dataList: Array,
    searchData: Array
  },
  data() {
    return {
      typeInput: 'friend',
      nameInput: '',
      searchAdd: []
    };
  },
  emits: ['dataListUpdated'],
  methods: {
    handleDatasAdded(searchAdd) {
      this.searchAdd = searchAdd
    },
    onSubmit() {
      const newDatas = this.dataList.slice();

      this.searchAdd.forEach(element => {
        const id = this.dataList.length > 0 ? +(newDatas.length) : 1;

        newDatas.findIndex(el => el.name === element.name) === -1 && newDatas.push({
          id: id,
          name: element.name,
          type: element.type,
          image: element.image
        });
      });
      this.$emit('dataListUpdated', newDatas);
    },
  }

}
</script>

<style scoped>
nav {
  width: 100%;
  height: 50px;

  display: flex;
  justify-content: end;
  align-items: center;
}

img {
  width: 70px;
}
</style>

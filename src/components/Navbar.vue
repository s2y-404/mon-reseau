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
              <div class="d-flex justify-content-between" style="width: 100%; padding: 1% 20% 4% 20%;">
                <div id="group-filtre" class="form-check form-check-inline">
                  <input class="form-check-input" type="radio" name="type" id="friend" v-model="typeInput" value="friend" @change="typeChange" checked />
                  <label class="form-check-label" for="friend">ami</label>
                </div>
                <div id="group-filtre" class="form-check form-check-inline">
                  <input class="form-check-input" type="radio" name="type" id="group" v-model="typeInput" value="group" @change="typeChange" />
                  <label class="form-check-label" for="group">groupe</label>
                </div>
              </div>
  
              <!-- CHOIX DE LA PHOTO DE PROFIL -->
              <div v-if="this.typeInput === 'friend'" class="d-flex justify-content-evenly" style="width: 75%;">
                <div class="p-0 input-img">
                  <input class="" type="radio" name="pp" id="pp_w_1" v-model="ppInput" value="pp_w_1" checked />
                  <label class="" for="pp_w_1">
                    <img src="@/assets/pp_w_1.png" alt="photo femme 1">
                  </label>
                </div>
                <div class="p-0 input-img">
                  <input class="" type="radio" name="pp" id="pp_w_2" v-model="ppInput" value="pp_w_2" />
                  <label class="" for="pp_w_2">
                    <img src="@/assets/pp_w_2.png" alt="photo femme 2">
                  </label>
                </div>
                <div class="p-0 input-img">
                  <input class="" type="radio" name="pp" id="pp_m_1" v-model="ppInput" value="pp_m_1" />
                  <label class="" for="pp_m_1">
                    <img src="@/assets/pp_m_1.png" alt="photo homme 1">
                  </label>
                </div>
                <div class="p-0 input-img">
                  <input class="" type="radio" name="pp" id="pp_m_2" v-model="ppInput" value="pp_m_2" />
                  <label class="" for="pp_m_2">
                    <img src="@/assets/pp_m_2.png" alt="photo homme 2">
                  </label>
                </div>
              </div>
              <div v-if="this.typeInput === 'group'" class="d-flex justify-content-evenly " style="width: 75%;">
                <div class="p-0 input-img">
                  <input class="" type="radio" name="pp" id="pp_g" v-model="ppInput" value="pp_g" checked />
                  <label class="" for="pp_g">
                    <img src="@/assets/pp_g.png" alt="photo group">
                  </label>
                </div>
                <div class="p-0 input-img">
                  <input class="" type="radio" name="pp" id="pp_a" v-model="ppInput" value="pp_a" />
                  <label class="" for="pp_a">
                    <img src="@/assets/pp_a.png" alt="photo groupe admin">
                  </label>
                </div>
              </div>
            </div>


            <!-- INPUT TEXT -->
            <div class="input-group flex-nowrap" style="margin: 5% 0;">
              <span class="input-group-text" id="nameInput"><i class="fa-solid fa-magnifying-glass"></i></span>
              <input type="text" class="form-control" placeholder="pseudo ou nom de groupe" v-model="nameInput" required />
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
    nbInvitation: String,
    datas: Array
  },
  data() {
    return {
      typeInput: 'friend',
      ppInput: 'pp_w_1',
      nameInput: ''
    };
  },
  emits: ['datas-updated'],
  methods: {
    typeChange() {
      this.ppInput = document.querySelector('input[name="pp"]:checked').value;
    },
    onSubmit() {
      console.log(`type: ${this.typeInput}\npp: ${this.ppInput}`);

      const newDatas = this.datas.slice();
      const id       = this.datas.length > 0 ? +(this.datas[newDatas.length - 1].id) + 1 : 1;
      const img      = this.ppInput;
      const type     = (this.ppInput === 'pp_a') ? 'admin' : this.typeInput
      const name     = this.nameInput

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

img {
  width: 70px;
}

.input-img input[type=radio]:checked + label>img {
  border: 3px solid blue;
  border-radius: 50%;
}
.input-img {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.input-img input {
  display: none;
}
</style>

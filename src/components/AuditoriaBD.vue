<template>
  <div>Auditoria BD</div>
  <!-- Botones de auditar y desauditar -->
  <div class="botones">
    <button class="button" @click="auditar" :disabled="sent">Auditar</button>
    <button class="button" @click="desauditar" :disabled="sent">Desauditar</button>
  </div>
</template>

<script>
import managerController from "../controllers/managerController";
import Swal from 'sweetalert2';
export default {
  data() {
    return {
      sent: false,
    };
  },
  methods: {
    auditar: async function () {
      this.sent = true;
      await managerController
        .auditar()
        .then((res) => {
          console.log(res);
          Swal.fire('', "Auditoria activada", 'success');
          this.sent = false;
        })
        .catch((error) => {
          console.error(error);

          this.sent = false;
        });
    },
    desauditar: async function () {
      this.sent = true;
      await managerController
        .desauditar()
        .then((res) => {
          console.log(res);
          Swal.fire('', "Auditoria desactivada", 'success');
          this.sent = false;
        })
        .catch((error) => {
          console.error(error);
          this.sent = false;
        });
    },
  },
};



</script>

<style>
.botones {
  display: flex;
  justify-content: space-around;
  margin-top: 20px;

 
}
.button {
    width: 90px;
    height: 50px;
    border-radius: 10px;
    border: none;
    background-color: #da5b07;
    color: white;
    font-size: 20px;
    font-weight: bold;
    cursor: pointer;
  }
</style>
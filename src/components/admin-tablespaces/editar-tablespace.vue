<template>
  <div>
    <label for="">Tipo de Tablespace a cambiar tamaño</label>
    <br /><br />
    <select id="seleccionar" ref="comboBoxT" @change="handleBoxChange">
      <option value="default" selected="Selected" disabled>
        --Seleccione un tipo de tablespace--
      </option>
      <option value="1">Tablespace</option>
      <option value="2">Temporary Tablespace</option>
    </select>
    <br /><br />
    <button @click="elegirTipo">Elegir Tipo</button>

    <br /><br />
    <section v-if="opcion && !chosenAgain">
      <label for="">Tablespace</label>
      <br /><br />
      <select @change="elegirSchema">
        <option value="default" selected="Selected" disabled>
          --Seleccione un tablespace--
        </option>
        <option
          v-for="(tablespace, index) in tablespaces"
          :key="index"
          :value="tablespace.tablespace_name"
        >
          {{ tablespace.tablespace_name }}
        </option>
      </select>

      <br /><br />
      <label for="">Tamaño del tablespace en MegaBytes</label>
      <br /><br />
      <input
        type="number"
        id="nombre_tbotemp"
        placeholder="Digite el tamaño"
        v-model="tamaño"
        @change="handleTextChange"
      />
      <br /><br />
      <button @click="cambiarTamano()">Editar tamaño</button>
    </section>
  </div>
</template>

<script>
import managerController from "../../controllers/managerController";
import Swal from 'sweetalert2';

export default {
  data() {
    return {
      tamaño: 0,
      opcion: null,
      chosenAgain: false,
      tablespaces: [],
      tablespace_elegido: null,
      sent: false,
    };
  },
  async mounted() {
    await managerController
      .getTablespaces()
      .then((response) => {
        this.tablespaces = response;
      })
      .catch((error) => console.error(error));
  },
  methods: {
    handleBoxChange: function (e) {
      this.opcion = e.target.value;
      this.chosenAgain = true;
      
    },
    elegirSchema: function (e) {
      this.tablespace_elegido = e.target.value;
    },
    elegirTipo: function () {
      this.chosenAgain = false;
      
    },
    cambiarTamano: async function () {
      this.sent = true;
      switch (this.opcion) {
        case "1":
          await managerController.resizeTablespace(this.tablespace_elegido, this.tamaño)
            .then((status) => {
                this.tablespace = "";
                this.tamaño = 0;
                Swal.fire("", status.route, "success");
            })
            .catch((error) => console.error(error,"error"));
          break;
        case "2":
          await managerController
            .resizeTemporaryTablespace(this.tablespace_elegido, this.tamaño)
            .then((response) => {
                this.tablespace = "";
                this.tamaño = 0;
                Swal.fire("", response.route, "success");
            
            })
            .catch((error) => console.error(error));
          break;
        default:
          break;
      }
    },
  },
};
</script>

<style scoped>
@import url(https://fonts.googleapis.com/css?family=Source+Sans+Pro);

body {
  background: #ffffff;
  color: #414141;
  font: 400 17px/2em "Source Sans Pro", sans-serif;
}

.select-box {
  position: relative;
  max-width: 20em;
  margin: 5em auto;
  width: 100%;
}

input,
select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

button {
  width: 100%;
  background-color: #ff3f0f;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #ff3f0f;
}
label,
footer {
  font-family: sans-serif;
}

label {
  font-size: 1rem;
  padding-right: 10px;
}

footer {
  font-size: 0.8rem;
  position: absolute;
  bottom: 30px;
  left: 30px;
}
</style>
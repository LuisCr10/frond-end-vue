<template>
  <div>
    <label class="label select-box1"
      ><span class="label-desc">Seleccione una tabla o schema</span>
    </label>
    <br /><br />
    <select @change="cambiarEleccion" name="respaldos" id="select-box1">
      <option value="default" selected="Selected" disabled>
        --Seleccione un tipo de estadistica--
      </option>
      <option value="1">Schema</option>
      <option value="2">Tabla</option>
    </select>
    <br /><br />
    <select @change="elegirSchema">
      <option value="default" selected="Selected" disabled>
        --Seleccione un schema--
      </option>
      <option
        v-for="(schema, index) in schemas"
        :key="index"
        :value="schema.schema_name"
      >
        {{ schema.schema_name }}
      </option>
    </select>
    <br /><br />
    <select v-if="!bandera" @change="elegirTabla">
      <option value="default" selected="Selected" disabled>
        --Seleccione un tablespace--
      </option>
      <option
        v-for="(tabla, index) in tablas"
        :key="index"
        :value="tabla.table_name"
      >
        {{ tabla.table_name }}
      </option>
    </select>
    <br /><br />
    <button v-on:click="hacerEstadisticas" type="submit">
      Hacer Estadisticas
    </button>
  </div>
</template>

<script>
import managerController from "../../controllers/managerController";
import Swal from 'sweetalert2';

export default {
  data() {
    return {
      schemas: [],
      schema_elegido: null,
      tablas: [],
      tabla_elegida: null,
      bandera: false,
    };
  },
  async mounted() {
    await this.cargarSchemas();
  },
  methods: {
    cambiarEleccion: async function (e) {
      if (e.target.value === "1") {
        this.bandera = true;
      } else {
        this.bandera = false;
      }
      await this.cargarSchemas();
    },
    cargarSchemas: async function () {
      await managerController
        .getSchemas()
        .then((res) => {
          this.schemas = res;
        })
        .catch((error) => {
          console.error(error);
        });
    },
    elegirSchema: async function (e) {
      this.schema_elegido = e.target.value;
      await this.cargarTablas();
    },
    cargarTablas: async function () {
      await managerController
        .getTablesFromSchema(this.schema_elegido)
        .then((res) => {
          this.tablas = res;
        })
        .catch((error) => {
          console.error(error);
        });
    },
    elegirTabla: async function (e) {
      this.tabla_elegida = e.target.value;
      await managerController
        .getColumnTables(this.schema_elegido, this.tabla_elegida)
        .then((res) => {
          this.columnas = res;
        })
        .catch((error) => console.error(error));
    },
    hacerEstadisticas: async function () {
      if (this.bandera) {
        await managerController
          .doEstadisticasSchema(this.schema_elegido)
          .then((res) => {
            Swal.fire('', "Estidistica creada correctamente", 'success');
            console.log(res);
          })
          .catch((error) => console.error(error));
      } else {
        await managerController
          .doEstadisticasTabla(this.schema_elegido, this.tabla_elegida)
          .then((res) => {
            Swal.fire('', "Estidistica creada correctamente", 'success');
            console.log(res);
          })
          .catch((error) => console.error(error));
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
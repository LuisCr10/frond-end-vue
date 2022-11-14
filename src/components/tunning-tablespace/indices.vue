<template>
  <div>
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
    <select @change="elegirTabla">
      <option value="default" selected="Selected" disabled>
        --Seleccione una tabla--
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
    <select @change="elegirColumnas">
      <option value="default" selected="Selected" disabled>
        --Seleccione una Columna--
      </option>
      <option
        v-for="(col, index) in columnas"
        :key="index"
        :value="col.column_name"
      >
        {{ col.column_name }}
      </option>
      <br /><br />
    </select>
    <br /><br />
    <section v-if="columnas_elegidas.length != 0">
      <p>Columnas seleccionadas para el índice:</p>
      <ul>
        <li
          v-for="(item, index) in columnas_elegidas"
          :key="index"
          :value="item"
        >
          {{ item }}
        </li>
        <br /><br />
      </ul>
    </section>
    <button @click="hacerIndice" :disabled="sent || !schema_elegido">
      Realizar Indice
    </button>
  </div>
</template>

<script>
import managerController from "../../controllers/managerController";
import Swal from 'sweetalert2';

export default {
  data() {
    return {
      sent: false,
      schemas: [],
      schema_elegido: null,
      tablas: [],
      tabla_elegida: null,
      columnas: [],
      columnas_elegidas: [],
      repeated: [],
    };
  },
  async mounted() {
    await this.cargarSchemas();
  },

  methods: {
    hacerIndice: async function () {
      await managerController
        .createIndexOnTable(
          this.schema_elegido,
          this.tabla_elegida,
          this.columnas_elegidas
        )
        .then((res) => {
          console.log(res);
          Swal.fire('', res.data.message, 'success');
        })
        .catch((error) => {
          console.error(error);
        });
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
      this.columnas_elegidas = [];
      this.repeated = [];
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
        .then((response) => {
          this.columnas = response;
        })
        .catch((error) => console.error(error));
    },
    elegirColumnas: function (e) {
      /*this.columnas_elegidas.forEach((column) => {
        if (e.target.value === column) {
          return;
        }
      });*/
      if (!this.repeated.includes(e.target.value)) {
        this.columnas_elegidas = [...this.columnas_elegidas, e.target.value];
        this.repeated.push(e.target.value);
      } else {
        this.columnas_elegidas = this.columnas_elegidas.filter(
          (item) => item !== e.target.value
        );
        this.repeated = this.repeated.filter((item) => item !== e.target.value);
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
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
    <button @click="elegir" :disabled="!schema_elegido">Elegir schema</button>
    <br />
    <p>
      Nota: El schema no debe tener ninguna escritura en él para poder realizar
      la recuperación
    </p>
    <section v-if="eleccion_schema">
      <label class="label select-box1"
        ><span class="label-desc"
          >Introduzca el archivo .DMP para respaldar</span
        >
      </label>
      <br /><br />
      <input
        type="file"
        @change="fileChange"
        id="file"
        name="file0"
        ref="file"
      />
      <br /><br />
      <button @click="recuperarRespaldo" :disabled="sent || !schema_elegido">
        Recuperar Respaldo</button
      ><br />
      <br />
    </section>
  </div>
</template>

<script>
import managerController from "../../controllers/managerController";

export default {
  data() {
    return {
      schemas: [],
      schema_elegido: null,
      eleccion_schema: false,
      sent: false,
      file: "",
    };
  },
  async mounted() {
    await this.cargarSchemas();
  },
  methods: {
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
    recuperarRespaldo: async function () {
      this.sent = true;

      await managerController
        .doASchemaRestore(this.schema_elegido, this.file)
        .then((response) => {
          this.downloadFile(response, "LOG");

          managerController.deleteASchemaRestoreFile(this.schema_elegido);
        })
        .catch((error) => {
          console.error(error);
        });

      this.sent = false;
    },
    downloadFile: function (response, filename) {
      // It is necessary to create a new blob object with mime-type explicitly set
      // otherwise only Chrome works like it should
      var newBlob = new Blob([response.data]);

      // IE doesn't allow using a blob object directly as link href
      // instead it is necessary to use msSaveOrOpenBlob
      if (window.navigator && window.navigator.msSaveOrOpenBlob) {
        window.navigator.msSaveOrOpenBlob(newBlob);
        return;
      }

      // For other browsers:
      // Create a link pointing to the ObjectURL containing the blob.
      const data = window.URL.createObjectURL(newBlob);
      var link = document.createElement("a");
      link.href = data;
      link.download = filename + ".DMP";
      link.click();
      setTimeout(function () {
        // For Firefox it is necessary to delay revoking the ObjectURL
        window.URL.revokeObjectURL(data);
      }, 100);
    },
    elegirSchema: function (e) {
      this.schema_elegido = e.target.value;
      this.eleccion_schema = false;
    },
    elegir: function () {
      this.eleccion_schema = true;
    },
    fileChange() {
      this.file = this.$refs.file.files[0];
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
  background-color: #4caf50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
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
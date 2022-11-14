<template>
  <div>
    <label class="label select-box1"
      ><span class="label-desc">Elija el esquema</span>
    </label>
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
    <button type="submit">Hacer ExplainPlan</button>
  </div>
</template>

<script>
import managerController from "../../controllers/managerController";

export default {
  data() {
    return {
      schemas: [],
      schema_elegido: null,
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
    elegirSchema: async function (e) {
      this.schema_elegido = e.target.value;
      
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
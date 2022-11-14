<!-- <template>
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
      <button @click="elimanarRespaldo" :disabled="sent || !schema_elegido">
        Eliminar Respaldo
      </button>
    </div>
  </template>

  <script>
    import managerController from "../../controllers/managerController";
    import Swal from 'sweetalert2';

    //metodo de eliminar respaldo
    export default {
      data() {
        return {
          schemas: [],
          schema_elegido: null,
          sent: false,
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
        elegirSchema: function (e) {
          this.schema_elegido = e.target.value;
        },
        eliminarRespaldo: async function () {
          this.sent = true;

          await managerController
            .doASchemaBackUp(this.schema_elegido)
            .then((response) => {
              console.log("Se ha hecho el respaldo");
              this.downloadFile (response, "BACKUP");
              this.sent = false;
              Swal.fire('', 'Se ha creado el respaldo', 'success');
            })
            .catch((error) => {
              console.error(error);
              Swal.fire('', 'No se ha podido crear el respaldo', 'error');
            });
        },
      },
    };
</script> -->
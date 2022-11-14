<!-- Cual opcion desea eliminar el backup de schema, tablespace o table -->
<template>
    <!-- Eliminar backup -->
    <div class="select-box">
        <label class="label select-box1"
            ><span class="label-desc">Elija un tipo de backup que desea eliminar</span>
        </label>
        <br /><br />
        <select @change="cambiarEleccion" name="respaldos" id="select-box1">
            <option value="default" selected="Selected" disabled>
                --Seleccione un tipo de backup--
            </option>
            <option value="1">Schema</option>
            <option value="2">Tablespace</option>
            <option value="3">Tabla</option>
        </select>
        <br />
        <br />
        <button @click="elegir" :disabled="sent || !opcion">Elegir backup</button>
        <br />
        <br />
        <router-view v-if="sent"></router-view>
    </div>
</template>

<script>
export default {
    data() {
        return {
            opcion: null,
            sent: false,
        };
    },
    methods: {
        elegir: function () {
            this.sent = true;

            switch (this.opcion) {
                case "1":
                    this.$router.push("/eliminar-backup/schema");
                    break;
                case "2":
                    this.$router.push("/eliminar-backup/tablespace");
                    break;
                case "3":
                    this.$router.push("/eliminar-backup/tabla");
                    break;

                default:
                    break;
            }
        },
        cambiarEleccion: function (e) {
            this.opcion = e.target.value;
            this.sent = false;
        },
    },
};
</script>
<template>
    <div class="select-box">
      <label class="label select-box1"
        ><span class="label-desc">Elija el respaldo que desea realizar</span>
      </label>
      <br /><br />
      <select @change="cambiarEleccion" name="respaldos">
        <option value="default" selected="Selected" disabled>
          --Seleccione un tipo de respaldo--
        </option>
        <option value="1">Schemas</option>
        <option value="2">Tablas</option>
        <option value="3">Full</option>
      </select>
      <br />
      <br />
      <button @click="elegir" :disabled="sent || !opcion">
        Elegir Tipo Respaldo
      </button>
      <br />
      <br />
      <br />
      <router-view></router-view>
    </div>
  </template>
  
  <script>
  import managerController from "../../controllers/managerController";
  
  export default {
    data() {
      return {
        opcion: null,
        sent: false,
      };
    },
    methods: {
      elegir: function () {
        switch (this.opcion) {
          case "1":
            this.$router.push("/crear-respaldos/schemas");
            break;
          case "2":
            this.$router.push("/crear-respaldos/tablas");
            break;
          case "3":
            this.hacerRespaldo();
            break;
  
          default:
            break;
        }
      },
      hacerRespaldo: async function () {
        this.sent = true;
  
        await managerController

            
            managerController.deleteADatabaseBackUp();
          
          
      },
      downloadFile(response, filename) {
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
      cambiarEleccion: function (e) {
        this.opcion = e.target.value;
      },
    },
  };
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped>
  @import url(https://fonts.googleapis.com/css?family=Source+Sans+Pro);
  
  body {
    background: #ffffff;
    color: #000000;
    font: 400 17px/2em "Source Sans Pro", sans-serif;
  }
  
  .select-box {
    border-radius: 5px;
    background-color: #f2f2f2;
    padding: 20px;
    position: relative;
    max-width: 20em;
    margin: 5em auto;
    width: 100%;
  }
  
  label,
  footer {
    font-family: sans-serif;
  }
  
  label {
    font-size: 1rem;
    padding-right: 10px;
  }
  
  input[type="text"],
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
  
  footer {
    font-size: 0.8rem;
    position: absolute;
    bottom: 30px;
    left: 30px;
  }
  </style>
  
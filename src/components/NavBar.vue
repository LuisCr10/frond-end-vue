<template>
  <div id="navbar">
    <div id="half1">
      <div id="logonav">
        <button class="menu1">Menu</button>
      </div>
      <div><br /><br /></div>
      <div id="usuarios" tabindex="5">
        <router-link
          active-class="active-link"
          style="text-decoration: none; color: inherit"
          to="/admin-tablespaces"
        >
          <div class="txt">Administración de tablespaces</div>
        </router-link>
      </div>
      <div><br /><br /></div>
      <div id="usuarios" tabindex="7">
        <router-link
          active-class="active-link"
          style="text-decoration: none; color: inherit"
          to="/performance-bd"
        >
          <div class="txt">Performance de la base de datos</div>
        </router-link>
      </div>
      <div><br /><br /></div>
      <div id="usuarios" tabindex="6">
        <router-link
          active-class="active-link"
          style="text-decoration: none; color: inherit"
          to="/tunning-consultas"
        >
          <div class="txt">Tunning de consultas</div>
        </router-link>
      </div>
      <div><br /><br /></div>
      <div id="usuarios" tabindex="8">
        <router-link
          active-class="active-link"
          style="text-decoration: none; color: inherit"
          to="/auditoria-bd"
        >
          <div class="txt">Auditoria de la BD</div>
        </router-link>
      </div>
      <div><br /><br /></div>
      <div id="usuarios" tabindex="9">
        <router-link
          active-class="active-link"
          style="text-decoration: none; color: inherit"
          to="/seguridad-usuarios"
        >
          <div class="txt">Seguridad de usuarios</div>
        </router-link>
      </div>
      <div><br /><br /></div>
      <div id="tablero" tabindex="1">
        <router-link
          active-class="active-link"
          style="text-decoration: none; color: inherit"
          to="/crear-respaldos"
        >
          <div class="txt">Creación de respaldos</div>
        </router-link>
      </div>
      <!-- Elimnar respaldos -->
      <!-- <div><br /><br /></div>
      <div id="tablero" tabindex="2">
        <router-link
          active-class="active-link"
          style="text-decoration: none; color: inherit"
          to="/backup-bd"
        >
          <div class="txt">Eliminación de respaldos</div>
        </router-link>
      </div> -->
      <div><br /><br /></div>
      <div><br /><br /></div>
      <div><br /><br /></div>
      <div><br /><br /></div>
      <div><br /><br /></div>
      <div><br /><br /></div>
      <div><br /><br /></div>
    </div>
  </div>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@500&display=swap");
#navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: #aaa19f;
  color: rgb(0, 0, 0);
  font-family: "Inter", sans-serif;
  font-size: 1.2rem;
  font-weight: 500;
  z-index: 100;
}
.menu1{

  background-color: #e64a27;
  border: none;
  color: rgb(0, 0, 0);
  padding: 15px 32px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin: 4px 2px;
  
}

@font-face {
  font-family: League-Gothic;
  src: url("../assets/fonts/league-gothic.ttf");
}
body {
  margin: 0;
  padding: 0;
}
/* #navbar {
  background-color: #f4f3f8;
  border-right-color: #c4c4c4;
  display: flex;
  width: 100%;
} */

#SSC {
  font-size: 1.25vw;
  font-family: "Cabin", sans-serif;
  color: #e06144;
  justify-content: center;
  text-align: center;
  margin-top: 0;
  width: 100%;
}

#logonav {
  display: block;
  cursor: pointer;
  font-size: 1.25vw;
  font-family: "Cabin", sans-serif;
  color: #d45810;
  justify-content: center;
  text-align: center;
  margin-top: 0;
  width: 100%;
}

#menu {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  margin-top: 0;
  margin-bottom: 0;
  padding-top: 0;

}

#tablero {
  display: flex;
}

#tablero:focus .txt {
  color: #e64a27;;
}

#tablero:focus img {
  filter: invert(41%) sepia(35%) saturate(2683%) hue-rotate(178deg)
    brightness(93%) contrast(90%);
}

#tablero:hover .txt {
  color: #e64a27;;
}

#tablero:hover img {
  filter: invert(41%) sepia(35%) saturate(2683%) hue-rotate(178deg)
    brightness(93%) contrast(90%);
}

#tablero div {
  color: #000000;
  font-family: "Inter", sans-serif;
  font-size: 1vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-left: 2%;
  cursor: pointer;
}

#tablero img {
  margin-left: 6%;
  width: 20%;
  height: auto;
  cursor: pointer;
}

#tareas {
  display: flex;
}

#tareas:focus .txt {
  color: #e64a27;;
}

#tareas:focus img {
  filter: invert(41%) sepia(35%) saturate(2683%) hue-rotate(178deg)
    brightness(93%) contrast(90%);
}

#tareas:hover .txt {
  color: #e64a27;;
}

#tareas:hover img {
  filter: invert(41%) sepia(35%) saturate(2683%) hue-rotate(178deg)
    brightness(93%) contrast(90%);
}

#tareas div {
  font-family: "Inter", sans-serif;
  color: #000000;
  font-size: 1vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-left: 2%;
  cursor: pointer;
}

#tareas img {
  margin-left: 4%;
  width: 20%;
  height: auto;
  cursor: pointer;
}

#usuarios {
  display: flex;
}

.active-link #usuarios .txt {
  color: #e64a27;
}

.active-link #usuarios img {
  filter: invert(41%) sepia(35%) saturate(2683%) hue-rotate(178deg)
    brightness(93%) contrast(90%);
}

#usuarios:hover .txt {
  color: #e64a27;
}

#usuarios:hover img {
  filter: invert(41%) sepia(35%) saturate(2683%) hue-rotate(178deg)
    brightness(93%) contrast(90%);
}

#usuarios div {
  font-family: "Inter", sans-serif;
  color: #000000;
  font-size: 1vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-left: 2%;
  cursor: pointer;
  text-decoration: none;
}

#usuarios img {
  margin-left: 4%;
  width: 20%;
  height: auto;
  cursor: pointer;
}

#ajustes {
  display: flex;
  flex-direction: row;
  justify-content: left;
  margin-top: 7%;
}

#ajustes:focus .txt {
  color: #e64a27;
}

#ajustes:focus img {
  filter: invert(41%) sepia(35%) saturate(2683%) hue-rotate(178deg)
    brightness(93%) contrast(90%);
}

#ajustes:hover .txt {
  color: #e64a27;
}

#ajustes:hover img {
  filter: invert(41%) sepia(35%) saturate(2683%) hue-rotate(178deg)
    brightness(93%) contrast(90%);
}

#ajustes div {
  font-family: "Inter", sans-serif;
  color: #000000;
  font-size: 1vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-left: 2%;
  cursor: pointer;
}

#ajustes img {
  margin-left: 4%;
  width: 13%;
  height: auto;
  cursor: pointer;
}

#ayuda {
  display: flex;
}

#ayuda:focus .txt {
  color: #e64a27;
}

#ayuda:focus img {
  filter: invert(41%) sepia(35%) saturate(2683%) hue-rotate(178deg)
    brightness(93%) contrast(90%);
}

#ayuda:hover .txt {
  color: #e64a27;
}

#ayuda:hover img {
  filter: invert(41%) sepia(35%) saturate(2683%) hue-rotate(178deg)
    brightness(93%) contrast(90%);
}

#ayuda div {
  font-family: "Inter", sans-serif;
  color: #000000;
  font-size: 1vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-left: 2%;
  cursor: pointer;
}

#ayuda img {
  margin-left: 6%;
  width: 10%;
  height: auto;
  cursor: pointer;
}

#salir {
  display: flex;
}

#salir:hover .txt {
  color: #e64a27;
}

#salir:hover img {
  filter: invert(41%) sepia(35%) saturate(2683%) hue-rotate(178deg)
    brightness(93%) contrast(90%);
}

#salir div {
  font-family: "Inter", sans-serif;
  color: #000000;
  font-size: 1vw;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin-left: 2%;
  cursor: pointer;
}

#salir img {
  margin-left: 5%;
  width: 11%;
  height: auto;
  cursor: pointer;
}

#usuarios .txt {
  text-decoration: none;
  color: #000000;
}

/* Extra small devices (phones, 600px and down) */
@media only screen and (max-width: 600px) {
  #navbar {
    width: 100%; /* Se cambio de 15% a 100% porque salia pequeño */
    height: 8vh;
    display: flex;
    flex-direction: row;
    border-right-width: 0px;
    align-items: center;
  }
  #SSC {
    width: 0%;
  }

  .active-link {
    height: 100%;
    border-left-width: 0px;
    border-top-color: #e64a27;
    border-top-style: solid;
    border-top-width: 2px;
  }
  #logonav {
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin: 0%;
    height: auto;
    width: 10rem;
    cursor: pointer;
  }

  #menu {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }
  #buscador {
    display: none;
  }
  #half1 {
    display: flex;
    flex-direction: row;
    height: 100%;
  }
  #tablero {
    height: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;
  }
  #tareas {
    height: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;
  }
  #usuarios {
    height: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;
  }
  #tablero div {
    font-size: 0;
    margin-left: 0%;
  }
  #tareas div {
    font-size: 0;
    margin-left: 0%;
  }
  #usuarios div {
    font-size: 0;
    margin-left: 0%;
  }
  #tablero img {
    height: 100%;
    width: 35%;
    cursor: pointer;
  }
  #tareas img {
    height: 100%;
    width: 35%;
    cursor: pointer;
  }
  #usuarios img {
    height: 100%;
    width: 35%;
    cursor: pointer;
  }

  #tablero:focus {
    border-left-width: 0px;
    border-top-color: #e64a27;
    border-top-style: solid;
    border-top-width: 2px;
  }
  #tareas:focus {
    border-left-width: 0px;
    border-top-color: #e64a27;
    border-top-style: solid;
    border-top-width: 2px;
  }
  #usuarios:focus {
    border-left-width: 0px;
    border-top-color: #e64a27;
    border-top-style: solid;
    border-top-width: 2px;
  }
  #half2 {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    border-top-width: 0px;
    border-left-color: #000000;
    border-left-style: solid;
    border-left-width: 2px;
    height: 100%;
  }
  #ajustes {
    display: flex;
    flex-direction: row;
    justify-content: center;
    height: 100%;
    margin-top: 0%;
  }

  #ajustes:focus {
    border-left-width: 0px;
    border-top: solid;
    border-top-width: 2px;
    border-top-color: #e64a27;
  }

  #ajustes div {
    font-size: 0;
    margin-left: 2%;
    cursor: pointer;
    height: 100%;
  }

  #ajustes img {
    height: 100%;
    width: 40%;
    cursor: pointer;
  }

  #ayuda {
    display: flex;
    flex-direction: row;
    justify-content: center;
    height: 100%;
  }
  #ayuda:focus {
    border-left-width: 0px;
    border-top: solid;
    border-top-width: 2px;
    border-top-color: #e64a27;
  }
  #ayuda div {
    font-size: 0;
    cursor: pointer;
  }

  #ayuda img {
    height: 100%;
    width: 35%;
    cursor: pointer;
  }
  #salir {
    padding-bottom: 0%;
    padding-top: 0%;
    border-bottom-width: 0px;
    border-top-width: 0px;
    display: flex;
    flex-direction: row;
    justify-content: center;
    height: 100%;
    margin-top: 0%;
  }

  #salir div {
    font-size: 0;
    margin-left: 2%;
  }

  #salir img {
    margin-left: 5%;
    height: 100%;
    width: 40%;
  }
}
/* Small devices (portrait tablets and large phones, 600px and up) */
@media only screen and (min-width: 600px) {
  #navbar {
    width: 100%; /* Se cambio de 15% a 100% porque salia pequeño */
    height: 8vh;
    display: flex;
    flex-direction: row;
    border-right-width: 0px;
    align-items: center;
  }

  #SSC {
    width: 0%;
  }

  .active-link {
    height: 100%;
    border-left-width: 0px;
    border-top-color: #e64a27;
    border-top-style: solid;
    border-top-width: 2px;
  }

  #logonav {
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin: 0%;
    height: auto;
    width: 20%;
    cursor: pointer;
  }

  #menu {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }

  #buscador {
    display: none;
  }

  #half1 {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    height: 100%;
  }

  #tablero {
    height: 100%;
  }

  #tareas {
    height: 100%;
  }

  #usuarios {
    height: 100%;
  }

  #tablero:focus {
    border-left-width: 0px;
    border-top-color: #e64a27;
    border-top-style: solid;
    border-top-width: 2px;
  }

  #tareas:focus {
    border-left-width: 0px;
    border-top-color: #e64a27;
    border-top-style: solid;
    border-top-width: 2px;
  }

  #usuarios:focus {
    border-left-width: 0px;
  }

  #half2 {
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
    align-items: center;
    border-top-width: 0px;
    border-left-color: #020202;
    border-left-style: solid;
    border-left-width: 2px;
    height: 100%;
    width: 15rem;
  }

  #ajustes {
    display: flex;
    flex-direction: row;
    justify-content: center;
    height: 100%;
    margin-top: 0%;
  }

  #ajustes:focus {
    border-left-width: 0px;
    border-top: solid;
    border-top-width: 2px;
    border-top-color: #e64a27;
  }

  #ajustes div {
    font-size: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin-left: 2%;
    cursor: pointer;
    height: 100%;
  }

  #ajustes img {
    height: 100%;
    width: 2rem;
    cursor: pointer;
  }

  #ayuda {
    display: flex;
    flex-direction: row;
    justify-content: center;
    height: 100%;
  }

  #ayuda:focus {
    border-left-width: 0px;
    border-top: solid;
    border-top-width: 2px;
    border-top-color: #e64a27;
  }

  #ayuda div {
    font-family: "Inter", sans-serif;
    font-size: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    cursor: pointer;
  }

  #ayuda img {
    height: 100%;
    width: 1.8rem;
    cursor: pointer;
  }

  #salir {
    padding-bottom: 0%;
    padding-top: 0%;
    border-bottom-width: 0px;
    border-top-width: 0px;
    display: flex;
    flex-direction: row;
    justify-content: center;
    height: 100%;
    margin-top: 0%;
  }

  #salir div {
    font-size: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin-left: 2%;
  }

  #salir img {
    margin-left: 5%;
    height: 100%;
    width: 2rem;
  }
}
/* Medium devices (landscape tablets, 768px and up) */
@media only screen and (min-width: 768px) {
}
/* Large devices (laptops/desktops, 992px and up) */
@media only screen and (min-width: 992px) {
}
/* Extra large devices (large laptops and desktops, 1200px and up) */
@media only screen and (min-width: 1200px) {
  #navbar {
    width: 15%; 
    border-right-style: solid;
    border-right-width: 2px;
    flex-direction: column;
    justify-content: space-between;
    height: 100%;
  }

  #SSC {
    height: 2rem;
  }

  #logonav img {
    width: 100%;
    height: auto;
  }

  #logonav {
    flex-direction: row;
    justify-content: center;
    margin-top: 5%;
    width: 100%;
  }

  #tablero:focus {
    border-left-color: #e64a27;
    border-left-style: solid;
    border-left-width: 6px;
    border-top-width: 0px;
  }

  #tareas:focus {
    border-left-color: #e64a27;
    border-left-style: solid;
    border-left-width: 6px;
    border-top-width: 0px;
  }

  #usuarios:focus {
    border-top-width: 0px;
  }

  .active-link {
    border-left-color: #e64a27;
    border-left-style: solid;
    border-left-width: 9px;
    border-top-width: 2px;
    
    /* borde abajo ancho */
    border-bottom-width: 4px;
    border-bottom-color: #e64a27;
    border-bottom-style: solid;
    /* Borde derecha */
    border-right-width: 4px;
    border-right-color: #e64a27;
    border-right-style: solid;
  }

  #menu {
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
  }

  #buscador {
    flex-direction: column;
    justify-content: center;
    width: 100%;
  }

  #half1 {
    display: flex;
    flex-direction: column;
    justify-content: start;
  }

  #half2 {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: flex-start;
    border-top-color: #000000;
    border-top-style: solid;
    border-top-width: 2px;
    width: 100%;
    height: fit-content;
  }

  #ajustes {
    display: flex;
    flex-direction: row;
    justify-content: left;
    margin-top: 7%;
  }

  #ajustes:focus {
    border-left-color: #e64a27;
    border-left-style: solid;
    border-left-width: 6px;
    border-top-width: 0px;
  }

  #ajustes div {
    font-family: "Inter", sans-serif;
    color: #000000;
    font-size: 1vw;
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin-left: 2%;
    cursor: pointer;
  }

  #ajustes img {
    margin-left: 4%;
    width: 13%;
    height: auto;
    cursor: pointer;
  }

  #ayuda {
    display: flex;
    flex-direction: row;
    justify-content: left;
    width: 80%;
    height: auto;
  }

  #ayuda:focus {
    border-left-color: #e64a27;
    border-left-style: solid;
    border-left-width: 6px;
    border-top-width: 0px;
  }

  #ayuda:focus img {
    filter: invert(41%) sepia(35%) saturate(2683%) hue-rotate(178deg)
      brightness(93%) contrast(90%);
  }

  #ayuda div {
    font-family: "Inter", sans-serif;
    color: #000000;
    font-size: 1vw;
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin-left: 2%;
    cursor: pointer;
  }

  #ayuda img {
    margin-left: 6%;
    width: 11%;
    height: auto;
    cursor: pointer;
  }

  #salir {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: left;
    padding-bottom: 4%;
    padding-top: 4%;
    border-bottom-color: #000000;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-top-color: #000000;
    border-top-style: solid;
    border-top-width: 2px;
  }

  #salir div {
    font-family: "Inter", sans-serif;
    color: #000000;
    font-size: 1vw;
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin-left: 2%;
    cursor: pointer;
  }

  #salir img {
    margin-left: 5%;
    width: 11%;
    height: auto;
    cursor: pointer;
  }
}
</style>

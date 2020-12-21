<template>
<div class="todo">
<div id="Temporada">
    <h2>
        <span>Bienvenido a Nuestro Season Hotels</span>
    </h2>
    <div class="container">
    
    <table>
        <table class="table table-dark table-hover">
        <tr>
            <th>Id_temporada</th>
            <th>temporada</th>
            <th>fecha inicial</th>
            <th>fecha final</th>
            <th>precio base</th>
        </tr>

        <tr>
            <td>{{temporada.id_temporada}}</td>
            <td>{{temporada.temporada}}</td>
            <td>{{temporada.fecha_inicial}}</td>
            <td>{{temporada.fecha_final}}</td>
            <td>{{temporada.precio_base}}</td>
        </tr>
        </table>
        </table>
    

    <div>
        <b-table striped hover :items="temporada"></b-table>
    </div> 
    </div>
</div>
</div>
</template>

<script>
import axios from "axios";
export default {
name: "Temporada",
data: function () {
    return {
    temporada: null
    };
},
created: function () {
    this.username = this.$route.params.username; //Obtiene el nombre de usuario de localstorage
    let self = this; // captura el this en axios para usarlo
    axios
    .get("https://seasonhotel-api.herokuapp.com/Temporada")
      .then((response) => {     // se ejecuta cuando todo sale bien
        self.temporada = response.data;
})
.catch((error) => {
        alert("ERROR Servidor");
    });
},
};
</script>
<style>
.todo {
width: 100%;
height: 100%;
display: flex;
justify-content: center;
}

.todo h2 {
display: flex;
justify-content: center;
font-size: 60px;
padding: 50px;
}

td {
text-align: center;
}
th {
text-align: center;
}
table { 
justify-content: center;
width: 100%;
height: 100%;
}

td:first-child {
width: 2px;
}
</style>

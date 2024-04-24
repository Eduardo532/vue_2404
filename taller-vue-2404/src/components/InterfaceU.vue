<template>
    <div id="conteiner">

        <form action="">
            
            <div id="form">
                <label for="nombre">Nombre </label>
                <input type="text" name="nombre" id="nombre">
            </div>
            <div id ="form">
                <label for="apellido">Apellido </label>
                <input type="text" name="apellido" id="apellido">
            </div>
            <div id ="form">
                <button type="submit">Enviar</button>
                <button type="reset">Limpiar</button>
            </div>
        </form>


    <div id="datos">_</div>

        
    </div>
</template>






<script>
export default {
  name: 'InterfaceU'
  
}
</script>

<style>
#conteiner{
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 30px;
}
div#form{
    margin-top: 1%;
}

button{
    margin-left: 20px;
}

div#datos{
    margin-top: 2%
}
</style>
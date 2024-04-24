<template>
    <div id="conteiner">

        <form action="">
            
            <div id="form">
                <label for="nombre">Nombre: </label>
                <input type="text" v-model="nombre">
            </div>
            <div id ="form">
                <label for="apellido">Apellido </label>
                <input type="text" name="apellido" id="apellido">
            </div>
            <div id ="form">
                <button @click="">Enviar</button>
                <button type="reset">Limpiar</button>
            </div>
        </form>


    <div>
        
    </div>

        
    </div>
</template>

<script>
import { split } from 'core-js/fn/symbol'
import { ref, reactive, computed,watch } from 'vue'


const nombres = ref(['Jane Doe'])

  const selecionado = ref('')
  const prefijo = ref('')
  const first = ref('')
  const last = ref('')

  watch(selecionado,(name)=>{
    ;[last.value,first.value]=name.split(' ')
  })

  function enviar(){
    if (hasValidInput()){
        const fullName = `${last.value} ${first.value}`
        if(!nombres.includes(fullName)){
            nombres.push(fullName)
            first.value = last.value = ''
        }
    }
  }

  function editar(){
    if(hasValidInput()&& selecionado.value){
        const i = nombres.indexOf(selecionado.value)
        nombres[i]=selecionado.value=`${last.value} ${first.value}` 
    }
  }

  



</script>






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
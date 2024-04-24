<template>
    <div id="conteiner">

        <div>
            
            <div id="form">
                <label for="nombre">Nombre: </label>
                <input v-model="first">
            </div>
            <div id ="form">
                <label for="apellido">Apellido </label>
                <input v-model ="last">
            </div>
            <div id ="form">
                
            </div>
        </div>

        <select size="5" v-model="selecionado">
            <option v-for="name in filteredNames":key=name>{{ name }}</option>
        </select>
        

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

  const filteredNames = computed(() =>
  nombres.filter((n) =>
    n.toLowerCase().startsWith(prefijo.value.toLowerCase())
  )
)

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

  function eliminar(){
    if (selecionado.value){
        const i = nombres.indexOf(selecionado.value)
        nombres.splice(i,1)
        selecionado.value = first.value = last.value = ''
    }
  }

  function hasValidInput(){
    return first.value.trim()&& last.value.trim()
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
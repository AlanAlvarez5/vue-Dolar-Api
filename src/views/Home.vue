<template>
  <v-container>
    <v-row>
      <v-col>
        <v-card>
          <v-date-picker 
            v-model="fecha"
            full-width
            :min="minimo"
            :max="maximo"
            @change="getDolar(fecha)"
          ></v-date-picker>
        </v-card>
        <v-card color="error" dark>
          <v-card-text class="display-1 text-center">
            {{valor}}
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>

import  axios  from "axios"


  export default {
    name: 'Home',
    data(){
      return {
        fecha: new Date().toISOString().substr(0, 10),
        minimo: '1984',
        maximo: new Date().toISOString().substr(0, 10),
        valor: null
      }
    },
    methods: {

      async getDolar(dia){
        let arrayFecha = dia.split(['-'])
        arrayFecha = arrayFecha.reverse()
        let dmmyy = arrayFecha.join('-')
        try {


          let datos = await axios.get(`https://mindicador.cl/api/dolar/${dmmyy}`)
          if (datos.data.serie.length > 0){
            this.valor = await datos.data.serie[0].valor
          }else{
            this.valor = 'Sin Resultados'
          }

        } catch(error){
          // console.log(error)
        }
        finally{

        }

      },
    },
    created(){
      this.getDolar(this.fecha)
    }

  }
</script>

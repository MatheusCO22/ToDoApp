<template>
  <v-container>
    <v-layout align-center column>
      <v-card class="rounded panel">
        <v-layout row align-center justify-center>
          <v-flex xs11 text-xs-center class="card-title">
            Lista de Tarefas
          </v-flex>
          <Popup></Popup>
        </v-layout>
        <v-card-text style="padding-top:0;">
          <v-divider/>
          <v-expansion-panel focusable class="elevation-0">
            <v-expansion-panel-content
              v-for="(tarefa,i) in 5"
              :key="i"
            >
              <template v-slot:header>
                <div>Tarefa {{i+1}}</div>
              </template>
              <v-card>
                <v-card-text class="grey lighten-3">
                  
                </v-card-text>
              </v-card>
            </v-expansion-panel-content>
          </v-expansion-panel>
        </v-card-text>
      </v-card>
    </v-layout>
  </v-container>
</template>

<script>
import Popup from '../components/PopupAdd'
export default {
  data(){
    return{
      tarefas:[]
    }
  },
  methods:{

  },
  created(){

  },
  components:{
    Popup
  }
}
</script>

<style>
  .panel{
    width: 70%;
    min-width: 200px;
  }
</style>
<template>
  <v-flex xs1 class="dialog">
    <v-dialog v-model="dialog" persistent max-width="400px" @keydown.esc="close">
      <template v-slot:activator="{ on }">
        <v-btn flat icon color="green" v-on="on">
          <v-icon>add</v-icon>
        </v-btn>
      </template>
      <v-card style="border-radius:0px">
        <v-card-title>
          <v-flex xs12 text-xs-center class="top-dialog">
              Adicionar Tarefa
          </v-flex>
        </v-card-title>
          <v-card-text>
          <v-divider/>
          <v-form ref="form" v-model="valid" @submit.prevent="submit">
            <v-container grid-list-md>
              <v-layout wrap>
                <v-flex xs12>
                  <v-text-field v-model="form.title" label="Título" :rules="[rules.required]"/>
                </v-flex>
                <v-flex xs12>
                  <v-text-field v-model="form.description" label="Descrição" :rules="[rules.required]"/>
                </v-flex>
                <v-flex xs12>
                  <v-text-field mask="##/##/####" v-model="form.deadline" :rules="[rules.required]">
                    <template v-slot:label>
                      Data limite
                      <small style="font-weight:200">(DD/MM/AAAA)</small>
                    </template>
                  </v-text-field>
                </v-flex>
                <v-flex xs12>
                  <v-subheader class="subh">Prioridade</v-subheader>
                  <v-slider v-model="form.priority" min="1" max="3" thumb-label always-dirty ticks tick-size="2" :tick-labels="prioridades"/>
                </v-flex>
              </v-layout>
            </v-container>
          </v-form>
          <v-divider/>
        </v-card-text>
        <v-card-actions>
          <v-btn color="red" fab flat outline class="white--text" @click="close">
            <v-icon>close</v-icon>
          </v-btn>
          <v-spacer></v-spacer>
          <v-btn color="green" :disabled="!valid" fab flat outline class="white--text" @click="submit">
            <v-icon>check</v-icon>
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-flex>
</template>

<script>
  export default {
    data(){
      const defaultForm = Object.freeze({
        title:'', description:'', priority:1, deadline: ''
      })
      return{
        form: Object.assign({}, defaultForm),
        valid:false,
        dialog:false,
        prioridades:['BAIXA', 'MÉDIA', 'ALTA'],
        rules:{
          required: value => !!value || 'Campo obrigatório'
        }
      }
    },
    methods:{
      formatDate(date) {
        const [year, month, day] = date.split('-')
        return `${day}/${month}/${year}`
      },
      submit(){
        const {
          title,
          description,
          priority,
          deadline
        }=this.form

        const task = {
          title, description, priority, deadline
        }
        console.log(task)
      },
      close(){
        this.dialog = false
        this.resetForm()
      },
      resetForm(){
        this.$refs.form.reset()
      }
    }
  }
</script>

<style>
  .dialog{
    margin: 0px;
    padding: 0;
    max-width: 100% !important;
  }
  .top-dialog{
    margin-bottom:-20px;
    font-weight: 500;
    color: gray;
  }
  .subh{
    padding: 0;
  }
  .v-input--slider--thumb-label{
    font-weight: 300;
    font-size: 13px;
  }
</style>

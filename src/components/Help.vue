<template>
    <q-layout>

        <div slot="header" class="toolbar">

            <q-toolbar-title :padding="0">
                Controle Escolar
            </q-toolbar-title>

        </div>

        <button class="primary" v-link="'/'"> voltar</button>

        <div class="layout-view">

            HELP

        </div>

    </q-layout>
</template>

<script>
  import axios from 'axios'

  export default {
    data () {
      return {
        list: []
      }
    },
    mounted () {
      axios.get('http://127.0.0.1:8000/es/buscatodastarefas?id=56', {
        headers: {
          'Content-Type': 'application/json'
        }
      })
        .then((res) => {
          this.list = res.data.tarefas

          // alert(res.data.total)
          // alert(res.data.tarefas[0].usuario.id)

          console.log(this.list)
        })
    }
  }
</script>

<style>
    .layout-view {
        padding: 10px;
    }
</style>

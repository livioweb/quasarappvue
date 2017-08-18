<template>
    <q-layout>

        <div slot="header" class="toolbar">

            <q-toolbar-title :padding="0">
                Meu App Ninja de Estudos
            </q-toolbar-title>

        </div>

        <button class="primary" v-link="'/'"> voltar</button>

        <div class="layout-view">
            <h5>Dados Escolares </h5>

            <!-- <q-select
                     type="list"
                     v-model="select"
                     :options="selectOptions"
             ></q-select>-->


             <div class="list">
                 <div class="item" v-for="res in list">

                     <div class="item-content">
                         {{res.name}}
                     </div>



                 </div>


             </div>

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
      axios.get('http://192.168.99.11:3003/api/usuarios')
        .then((res) => {
          this.list = res.data
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

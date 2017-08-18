<template>
    <q-layout>

        <div slot="header" class="toolbar">

            <q-toolbar-title :padding="0">
                Controle Escolar
            </q-toolbar-title>

        </div>

        <button class="primary" v-link="'/'"> voltar</button>

        <div class="layout-view">
            <h5>Usuarios do Sistema</h5>

            <!-- <q-select
                     type="list"
                     v-model="select"
                     :options="selectOptions"
             ></q-select>-->




                    <table class="q-table responsive">
                        <thead>
                        <tr>
                            <th>PROGRAMADOR</th>
                            <th>NOVO</th>
                            <th>Em Andamento</th>
                        </tr>
                        </thead>

                        <tbody  v-for="res in list">
                        <tr>
                            <td data-th="Name">{{res.usuario.id}} {{res.usuario.nome}}</td>
                            <td data-th="Price">{{res.Novo.total}}</td>
                            <td data-th="In Stock">{{res.Em_andamento.total}}</td>
                        </tr>
                        </tbody>
                    </table>

                    <!--
                    <div class="item-content">
                        {{res.usuario.nome}}{{res.usuario.id}}
                    </div>
                    <div class="item-secondary">
                        {{res.id}}
                        <i class="material-icons"> {{res.id}} </i>

                    </div>
                    <div class="item-secondary">
                        {{res.id}}
                        <i class="material-icons"> {{res.id}} </i>

                    </div>
                    <div class="item-secondary">
                        {{res.id}}
                        <i class="material-icons"> {{res.id}} </i>

                    </div>-->









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
      axios.get('http://grievous.app/es/buscatodastarefas?id=56', {
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

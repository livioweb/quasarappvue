<template>
    <q-layout>

        <div slot="header" class="toolbar">

            <q-toolbar-title :padding="0">
                Meu App Ninja de Estudos
                v{{$q.version}}
            </q-toolbar-title>

        </div>

        <button class="primary" v-link="'/'"> voltar</button>

        <div class="layout-view">
            <h4>Ultimos 30 diretorios publicados</h4>


            <div class="list">
                <div class="item" v-for="repo in list">
                    <img :src="repo.owner.avatar_url" alt="" class="item-primary">

                    <div class="item-content">
                        {{repo.name}}
                    </div>

                    <div class="item-secondary">
                        <a :href="repo.html_url">
                            <i class="material-icons"> open_in_browser </i>
                        </a>
                    </div>

                </div>


            </div>

        </div>

    </q-layout>
</template>

<script>
  import axios from 'axios'
  let user = 'erikfig'

  export default {
    data () {
      return {
        list: []
      }
    },
    mounted () {
      axios.get('https://api.github.com/users/' + user + '/repos?direction=asc')
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

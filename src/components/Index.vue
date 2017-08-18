<template>

    <q-layout>
        <!-- Header -->
        <div slot="header" class="toolbar">
            <!-- opens left-side drawer using its ref -->
            <button class="hide-on-drawer-visible" @click="$refs.leftDrawer.open()">
                <i>menu</i>
            </button>
            <q-toolbar-title :padding="1">
                MOBINE - ForkRedmine
            </q-toolbar-title>
            <!-- opens right-side drawer using its ref -->
            <button class="hide-on-drawer-visible" @click="$refs.rightDrawer.open()">
                <i>menu</i>
            </button>
        </div>
        <!-- Navigation Tabs -->
        <q-tabs slot="navigation">
            <q-tab icon="album" route="/programadores" exact replace>Programadores</q-tab>
            <q-tab icon="album" route="/analistas" exact replace>Analistas</q-tab>
            <q-tab icon="alarm" route="/tarefas" exact replace>Tarefas</q-tab>

            <!-- <q-tab icon="album" route="/repos" exact replace>Repositorio</q-tab>
             <q-tab icon="alarm" route="/escola" exact replace>Escolas</q-tab>
             <q-tab icon="alarm" route="/users" exact replace>Usuarios</q-tab>-->

            <q-tab icon="help" route="/help" exact replace>Help</q-tab>
        </q-tabs>
        <!-- Left-side Drawer -->
        <q-drawer ref="leftDrawer">
            <div class="toolbar">
                <q-toolbar-title>
                    aplicativos
                </q-toolbar-title>
            </div>
            <div class="list no-border platform-delimiter">
                <q-drawer-link icon="mail" :to="{path: '/tarefas', exact: true}">
                    Tarefas
                </q-drawer-link>
            </div>
        </q-drawer>
        <!-- IF USING subRoutes only: -->
        <router-view class="layout-view"></router-view>
        <!-- OR ELSE, IF NOT USING subRoutes: -->
        <div class="layout-view">

            <div class="list">
                <div class="item" v-for="res in list">

                    <div class="row responsive-gutter">

                        <div class="auto">
                            <div class="card">
                                <div class="card-title bg-primary text-white">
                                    {{res.Novo.nome}}


                                    <q-tooltip>
                                        <div class="list item-delimiter highlight">
                                            <div
                                                    class="item item-link"
                                                    @click="doSomething(), $refs.popover.close()"
                                            >
                                                ...
                                            </div>
                                        </div>
                                    </q-tooltip>



                                </div>
                                <div class="card-content card-force-top-padding">
                                    {{res.Novo.total}}
                                </div>
                            </div>

                        </div>

                        <div class="auto">

                            <div class="card">
                                <div class="card-title bg-primary text-white">
                                    {{res.Em_andamento.nome}}
                                </div>
                                <div class="card-content card-force-top-padding">
                                    {{res.Em_andamento.total}}
                                </div>
                            </div>

                        </div>

                        <div class="auto">

                            <div class="card">
                                <div class="card-title bg-primary text-white">
                                    {{res.C_Implantacao.nome}}
                                </div>
                                <div class="card-content card-force-top-padding">
                                    {{res.C_Implantacao.total}}
                                </div>
                            </div>

                        </div>

                    </div>

                    <div class="row responsive-gutter">

                        <div class="auto">

                            <div class="card">
                                <div class="card-title bg-primary text-white">
                                    {{res.C_Feedback.nome}}
                                </div>
                                <div class="card-content card-force-top-padding">
                                    {{res.C_Feedback.total}}
                                </div>
                            </div>

                        </div>

                        <div class="auto">

                            <div class="card">
                                <div class="card-title bg-primary text-white">
                                    {{res.Correcao.nome}}
                                </div>
                                <div class="card-content card-force-top-padding">
                                    {{res.Correcao.total}}
                                </div>
                            </div>

                        </div>

                        <div class="auto">

                            <div class="card">
                                <div class="card-title bg-primary text-white">
                                    {{res.Resolvido.nome}}
                                </div>
                                <div class="card-content card-force-top-padding">
                                    {{res.Resolvido.total}}
                                </div>
                            </div>

                        </div>

                    </div>

                    <div class="row responsive-gutter">

                        <div class="auto">

                            <div class="card">
                                <div class="card-title bg-primary text-white">
                                    {{res.Interrompido.nome}}
                                </div>
                                <div class="card-content card-force-top-padding">
                                    {{res.Interrompido.total}}
                                </div>
                            </div>

                        </div>

                        <div class="auto">

                            <div class="card">
                                <div class="card-title bg-primary text-white">
                                    {{res.Feedback.nome}}
                                </div>
                                <div class="card-content card-force-top-padding">
                                    {{res.Feedback.total}}
                                </div>
                            </div>

                        </div>

                        <div class="auto">

                            <div class="card">
                                <div class="card-title bg-primary text-white">
                                    {{res.Em_espera.nome}}
                                </div>
                                <div class="card-content card-force-top-padding">
                                    {{res.Em_espera.total}}
                                </div>
                            </div>

                        </div>

                    </div>


                    <div class="row responsive-gutter">

                        <div class="auto">

                            <div class="card">
                                <div class="card-title bg-primary text-white">
                                    {{res.Fechado.nome}}
                                </div>
                                <div class="card-content card-force-top-padding">
                                    {{res.Fechado.total}}
                                </div>
                            </div>

                        </div>

                        <div class="auto">

                            <div class="card">
                                <div class="card-title bg-primary text-white">
                                    {{res.Rejeitado.nome}}
                                </div>
                                <div class="card-content card-force-top-padding">
                                    {{res.Rejeitado.total}}
                                </div>
                            </div>

                        </div>

                        <div class="auto">

                            <div class="card">
                                <div class="card-title bg-primary text-white">
                                    {{res.Melhoria.nome}}
                                </div>
                                <div class="card-content card-force-top-padding">
                                    {{res.Melhoria.total}}
                                </div>
                            </div>

                        </div>

                    </div>


                </div>

            </div>


        </div>
        <!-- Right-side Drawer -->
        <!-- <q-drawer ref="rightDrawer" right-side>
             ...
         </q-drawer>-->
        <!-- Footer -->
        <div slot="footer" class="toolbar">
            ....
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
      axios.get('http://127.0.0.1:8000/es/buscatodastarefasbox', {
        headers: {
          'Content-Type': 'application/json'
        }
      })
        .then((res) => {
          this.list = res.data.tarefas
          // alert(res.data.total)
          console.log(this.list)
        })
    }
  }
</script>

<style lang="stylus">
    .layout-view {
        padding: 10px;
    }
</style>

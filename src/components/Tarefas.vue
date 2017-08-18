<template>
    <q-layout>

        <div slot="header" class="toolbar">

            <q-toolbar-title :padding="0">
                MOBINE - ForkRedmine
            </q-toolbar-title>

        </div>

        <button class="primary" v-link="'/'"> voltar</button>

        <div class="layout-view">
            <h5>Lista de tarefas de todos usuarios</h5>


            <table class="q-table responsive bordered highlight loose">
                <thead >
                <tr>
                    <th>PROGRAMADOR</th>
                    <th>TOTAL</th>
                    <th>NOVO</th>
                    <th>Em Andamento</th>
                    <th>C. Implantação</th>
                    <th>C. Feedback</th>
                    <th>Correção</th>
                    <th>Resolvido</th>
                    <th>Interrompido</th>
                    <th>Feedback</th>
                    <th>Em espera</th>
                    <th>Fechado</th>
                    <th>Rejeitado</th>
                    <th>Melhoria</th>

                </tr>
                </thead>

                <tbody  v-for="res in list" >
                <tr>
                    <td data-th="Usuario">{{res.usuario.id}} {{res.usuario.nome}}</td>
                    <td data-th="TOTALp">Total</td>
                    <td :data-th=res.Novo.nome>{{res.Novo.total}}</td>
                    <td :data-th=res.Em_andamento.nome >{{res.Em_andamento.total}}</td>
                    <td :data-th=res.C_Implantacao.nome >{{res.C_Implantacao.total}}</td>
                    <td :data-th=res.C_Feedback.nome>{{res.C_Feedback.total}}</td>
                    <td :data-th=res.Correcao.nome>{{res.Correcao.total}}</td>
                    <td :data-th=res.Resolvido.nome>{{res.Resolvido.total}}</td>
                    <td :data-th=res.Interrompido.nome>{{res.Interrompido.total}}</td>
                    <td :data-th=res.Feedback.nome>

                        <q-tooltip>
                        <div class="list item-delimiter highlight">
                            <div
                                    class="item item-link"
                                    @click="doSomething(), $refs.popover.close()"
                            >
                                {{res.Feedback.tarefas}}
                            </div>
                        </div>
                        </q-tooltip>

                        {{res.Feedback.total}}</td>
                    <td :data-th=res.Em_espera.nome>{{res.Em_espera.total}}</td>
                    <td :data-th=res.Fechado.nome>{{res.Fechado.total}}</td>
                    <td :data-th=res.Rejeitado.nome>{{res.Rejeitado.total}}</td>
                    <td :data-th=res.Melhoria.nome>{{res.Melhoria.total}}</td>
                </tr>
                </tbody>
            </table>

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
      axios.get('http://127.0.0.1:8000/es/buscatodastarefas', {
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

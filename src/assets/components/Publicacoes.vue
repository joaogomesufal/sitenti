<template>
  <div id="publicacoes" class="section">
    <v-container>
      <v-layout row>
        <v-flex md12 class="section-title">
          <h3>Publicações</h3>
          <p>Trabalhos desenvolvidos por membros do NTI.</p>
        </v-flex>
      </v-layout>

      <v-layout row wrap class="plus" v-for="setor in setores" v-bind:key="setor.nome">
        <v-flex sm12 xs12 md4 class="employee" v-for="integrante in setor.integrantes" v-bind:key="integrante.nome">
          <div class="employee-avatar">
            <img :src="integrante.imagem" alt="">
          </div>
          <div class="employee-description">
            <h3 class="name">{{integrante.nome}}</h3>
            <h4 class="function">{{integrante.cargo}}</h4>
          </div>
        </v-flex>
      </v-layout>

    </v-container>
  </div>
</template>

<script>
    export default {
        name: "Publicacoes.vue",
        data() {
          publications: [
            {
              title: '',
              description: '',
              url: ''
            },

            {
              title: '',
              description: '',
              url: ''
            },

            {
              title: '',
              description: '',
              url: ''
            },

            {
              title: '',
              description: '',
              url: ''
            },

            {
              title: '',
              description: '',
              url: ''
            }
          ]
        }
    }
</script>

<style scoped>

</style>

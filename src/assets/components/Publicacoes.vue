<template>
  <div id="publicacoes" class="section">
    <v-container>
      <v-layout row>
        <v-flex md12 class="section-title">
          <h3>Publicações</h3>
          <p>Trabalhos desenvolvidos por membros do NTI.</p>
        </v-flex>
      </v-layout>

      <v-layout row wrap>
        <v-flex xs12 sm6 md4 lg3 v-for="(publication, index) in publications" v-bind:key="index">
          <v-card class="publication-card" flat>
            <v-card-title>
              <a :href="publication.url">
                <v-icon>picture_as_pdf</v-icon>
                <span>Acessar:</span>
                {{publication.title}}
                ({{publication.year}})
              </a>
            </v-card-title>
          </v-card>
        </v-flex>
      </v-layout>

    </v-container>
  </div>
</template>

<script>
    import pdf from 'vue-pdf'
    import publications_data from '../data/publications'
    const { publications } = publications_data
    export default {
        name: "Publicacoes.vue",
        components: {
          pdf
        },
        data() {
          return {
            publications: publications
          }
        }
    }
</script>

<style lang="scss">
  .v-card.publication-card {
    background: rgb(4, 32, 56);
    min-height: 120px;
    margin: 10px;

    .v-card__title {



      a {
        text-decoration: none;
        color: #64D2C9;
        font-size: 16px;
        font-weight: 300;

        &:active,&:focus,&:hover,&select {
          background: #14558C;
        }

        i {
          color: crimson;
        }

        span {
          font-weight: bold;
          color: white;
        }
      }
    }


  }
</style>

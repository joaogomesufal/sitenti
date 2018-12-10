<template>
  <div id="header-menu">
    
    <v-navigation-drawer id="side-menu" v-model="sideNav" app>
      <v-list>
        <v-list-tile v-for="item in menuItems" :key="item.title">
          <v-list-tile-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-tile-action>
          <a :href="item.href"><v-list-tile-content>{{ item.title }}</v-list-tile-content></a>
        </v-list-tile>
        <v-list-tile @click.native.stop="sideNav = !sideNav" class="close-side">
          <v-list-tile-action>
            <v-icon>close</v-icon>
          </v-list-tile-action>
          <v-list-tile-content>Fechar</v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>

    

    <v-toolbar id="menu">
      <v-toolbar-side-icon @click.native.stop="sideNav = !sideNav">
        <v-icon>menu</v-icon>
      </v-toolbar-side-icon>
      <v-spacer></v-spacer>
      <v-toolbar-items id="menu-itens">
        <v-btn flat v-for="item in menuItems" :key="item.title" :href="item.href" v-smooth-scroll>
          <v-icon left>{{ item.icon }}</v-icon>
          {{ item.title }}
        </v-btn>

      </v-toolbar-items>
    </v-toolbar>

    <div id="header">
      <v-container>
        <v-layout row wrap >
          <v-flex md6 xs12 class="header-element">
            <div class="header-element-logo">
              <img src="../images/logo-nti.png">
            </div>
            <div class="header-elemente-content">
              <h3>Núcleo de Tecnologia da Inforamção</h3>
              <h4>Campus Arapiraca</h4>
            </div>
          </v-flex>

          <v-flex md6 xs12 class="header-element">
            <div class="header-element-logo">
              <img src="../images/logo-ufal.png">
            </div>
            <div class="header-elemente-content">
              <h3>Universidade Federal de Alagoas</h3>
              <h4>Campus Arapiraca</h4>
            </div>
          </v-flex>
        </v-layout>
      </v-container>
    </div>
  </div>
</template>

<script>
  import * as easings from 'vuetify/es5/util/easing-patterns'

  export default {
    data () {
      return {
        sideNav: false,
        menuItems: [
          {icon: 'home', title: 'Início', href: '#'},
          {icon: 'widgets', title: 'Utilítários', href: '#utilitarios'},
          {icon: 'import_contacts', href: '', title: 'Serviços', href: '#catalogo-servicos'},
          {icon: 'group',title: 'Equipe', href: '#equipe'},
        ],
      }
    },
  }
</script>

<style scoped>

</style>

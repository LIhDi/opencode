<template>
  <div>
    <v-toolbar height="37" flat color="grey lighten-4">
      <v-spacer></v-spacer>
      <v-btn class="transparent pink--text" @click="mostrarLista = !mostrarLista" icon><v-icon>mdi-apps</v-icon></v-btn>
      <v-btn class="transparent pink--text" @click="mostrarLista = !mostrarLista" icon><v-icon>mdi-format-list-bulleted</v-icon></v-btn>
    </v-toolbar>
    <v-container fluid >
      <v-layout row wrap>
        <v-flex xs0 sm0 md3 class="pt-0 ml-4 hidden-xs-only">
          <BlogOptionsLeft/>
        </v-flex>
        <BlogListTutorial v-if="!mostrarLista"/>
        <v-flex v-if="mostrarLista" xs12 sm12 md8 class="pt-5">
          <v-toolbar :v-if="true" :style="'border-color:'+post.color" v-for="post in ListTutoriais" :key="post.title" flat>
            <v-toolbar-title>
              <span class="subheading">{{post.title}}</span><br/>
              <span class="caption grey--text">Por: {{post.autor}}{{post.data}}</span>
            </v-toolbar-title>
            <v-spacer></v-spacer>
            <div class="hidden-xs-only">
            <v-icon class="mr-2 grey--text" small >mdi-comment-multiple</v-icon>
            <span class="mr-3 grey--text caption">{{post.comentarios}}</span>
            <v-icon class="mr-1 grey--text" small>mdi-eye</v-icon>
            <span class="caption grey--text mr-2">{{post.visitados}}</span>
            <v-btn small class="caption" flat outline :color="post.color">
              {{post.tipo}}
            </v-btn>
            </div>
         </v-toolbar>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>
<script>
import ListTutoriais from '~/contents/listTutoriais.js'
import BlogOptionsLeft from "~/components/tutoriais/BlogOptionsLeft"
import BlogListTutorial from "~/components/tutoriais/BlogListTutorial"
export default {
  components: { BlogOptionsLeft, BlogListTutorial },
  data () {
    return {
      ListTutoriais,
      mostrarLista: false
    }
  },
  methods: {
  }
}
</script>
<style scoped>
.theme--light.v-toolbar {
  background-color: transparent;
}
.theme--light.v-toolbar:hover {
  background-color: #F5F5F5;
}
.v-btn{
  border-radius: 50px;
}
.v-toolbar{
  border-left-style: solid;
  border-left-width: 3px;
}
</style>

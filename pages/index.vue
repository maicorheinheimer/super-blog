<template>
  <div class="w-1/2 mx-auto my-20">
    <h1 class="text-3xl font-semibold text-red-600">
      {{tituloBlog}}
    </h1>
    <article v-for="(artigo, id) in listaArtigos" :key="id" class="my-20">
      <h2 class="text-5xl font-semibold mb-5">{{artigo.email}}</h2>
      <p class="mb-5">{{artigo.name}}</p>
      <p class="text-red-500">Ler Mais</p>
    </article>
  </div>
</template>

<script>
export default {
  data() {
    return {
      listaArtigos: [],
      tituloBlog: "Super Blog",
    };
  },
  created(){
    this.carregarListaArtigos();  
  },
  methods: {
    carregarListaArtigos() {
      this.$axios
        .get("https://jsonplaceholder.typicode.com/comments")
        .then((respostaAPI) => {
          this.listaArtigos = respostaAPI.data;   
        });
    },
  },
};
</script>

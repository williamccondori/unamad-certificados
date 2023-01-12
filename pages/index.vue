<template>
  <v-row align="center">
    <v-col cols="12">
      <v-text-field
        v-model="query"
        solo
        append-icon="mdi-magnify"
        label="Ingrese sus nombres y apellidos..."
        @input="search()"
      />
    </v-col>
    <v-col
      v-for="participant in results"
      :key="participant.id"
      cols="12"
      xs="6"
      sm="6"
      md="4"
      lg="3"
    >
      <DescriptionCard :participant="participant" />
    </v-col>
  </v-row>
</template>

<script>
import DescriptionCard from "@/components/DescriptionCard.vue";
export default {
  name: "IndexPage",
  components: {
    DescriptionCard,
  },
  data() {
    return {
      participants: [],
      results: [],
      query: "",
    };
  },
  async fetch() {
    const data = await fetch("/data.json");
    this.participants = await data.json();
  },
  head: {
    title: "Buscador",
  },
  methods: {
    search() {
      this.results = [];
      if (this.query && this.query.length > 3) {
        const query = this.query?.toLowerCase();
        this.results = this.participants.filter(
          (x) => x.name?.toLowerCase().indexOf(query) > -1
        );
      }
    },
  },
};
</script>

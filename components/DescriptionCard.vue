<template>
  <v-card v-if="participant" min-height="500">
    <v-img
      height="250"
      :src="`https://ui-avatars.com/api/?format=svg&name=${participant.nombresApellidos}`"
    />
    <v-card-title> {{ participant.nombresApellidos }} </v-card-title>
    <v-card-text>
      <p>
        <b>{{ participant.condicion }}</b>
      </p>
      <p>{{ participant.institucion }}</p>
    </v-card-text>
    <v-divider class="mx-4" />
    <v-card-actions>
      <v-btn text @click="download(participant.enlaceWeb)">
        Descargar certificado
      </v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  props: {
    participant: {
      type: Object,
      required: true,
    },
  },
  methods: {
    download(url) {
      window.open(url, "_blank");
    },
  },
};
</script>

<template>
  <v-card v-if="participant" min-height="500">
    <v-img
      height="250"
      :src="`https://ui-avatars.com/api/?format=svg&name=${participant.name}`"
    />
    <v-card-title> {{ participant.name }} </v-card-title>
    <v-card-text>
      <p>
        <b>{{ participant.condition }}</b>
      </p>
      <p>{{ participant.institution }}</p>
      <p>
        Código de descarga: <br />
        👉 <b>{{ participant.code }}</b>
      </p>
    </v-card-text>
    <v-divider class="mx-4" />
    <v-card-actions>
      <v-btn block color="primary" @click="copyAndOpen(participant.code)">
        Copiar código e ingresar
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
    copyAndOpen(code) {
      navigator.clipboard.writeText(code);
      window.open("https://sgd.unamad.edu.pe/consultas/constancias", "_blank");
    },
  },
};
</script>

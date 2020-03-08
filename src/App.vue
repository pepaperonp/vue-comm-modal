<template>
  <v-app>
    <v-content>
      <br/>
      <FormDialog/>
    </v-content>
  </v-app>
</template>

<script>
import FormDialog from './components/FormDialog';

export default {
  name: 'App',

  components: {
    FormDialog,
  },
};
</script>

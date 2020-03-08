<template>
  <v-row justify="center">
    <v-dialog v-model="dialog" persistent max-width="200">
      <v-card justify="center">
        <v-card-title class="headline"></v-card-title>
        <v-row style="width:100%">
          <v-col md="12" align="center">
            <div style="margin-left:15px">{{msg}}</div>
          </v-col>
        </v-row>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="green darken-1" text @click="no()">No</v-btn>
          <v-btn color="green darken-1" text @click="yes()">Yes</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-row>
</template>

<script>

  export default {
    props: ['msg','isOpen','doYes','doNo'],
    data () {
      return {
        dialog: false
      }
    },
    watch: {
      isOpen: function (val) {
        this.dialog = val
      }
    },
    methods: {
      yes () {
        this.doYes()
        this.dialog = false
      },
      no () {
        this.doNo()
        this.dialog = false
      }
    }
  }
</script>

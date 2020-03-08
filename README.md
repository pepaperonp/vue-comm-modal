## Vue & Vuetify CommonDialog

<a href="https://r2vqi.csb.app/" target="_blank">DEMO</a>

In the project directory, you can run:

### `yarn serve` or `npm run serve`

Runs the app in the development mode.<br />
Open [http://localhost:8080](http://localhost:8080) to view it in the browser.

### `<CommonDialog ... />`
```vue
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
    props: {
      msg: String,
      isOpen: Boolean,
      doYes: Function,
      doNo: Function,
    },
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
```
### How To Use.
```vue
    <CommonDialog
            :msg="dlg.msg"
            :is-open="dlg.isOpen"
            :do-yes="dlg.doYes"
            :do-no="dlg.doNo"
    />
```

```vue
<template>
  <v-btn text @click="dlg.isOpen=true">do</v-btn>
</template>
<script>
    export default {
        data() {
          return {
            dlg: {
              msg: 'Message',
              isOpen: false,
              doYes: ()=>{
                ...
                this.dlg.isOpen=false
              },
              doNo: ()=>{
                this.dlg.isOpen=false
              }
            }
          }
        }
    }
</script>
```

### License
This project is 
<a href="https://opensource.org/licenses/MIT">MIT licensed.</a>
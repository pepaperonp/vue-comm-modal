<template>
  <div>
  <v-card
    class="mx-auto"
    max-width="800"
    style="height:200px"
  >
    <v-row justify="center">
      <v-dialog v-model="dialog" persistent max-width="300">
        <template v-slot:activator="{ on }">
          <v-container>
            <v-row justify="center">
              <h2 style="margin-top:30px">
                埼玉県人にはそこらへんの草でも食わせておけ
              </h2>
            </v-row>
            <v-row justify="center">
              <v-btn color="primary" style="margin-top:20px" dark v-on="on">Open</v-btn>
            </v-row>
          </v-container>
        </template>
        <v-card>
          <v-card-title class="headline">Vuetify</v-card-title>
          <v-divider />
          <br/>
          <br/>
          <v-container>
            <v-row style="width:100%">
              <v-col md="12" style="margin-left:10px">
                <v-text-field
                  label="Email"
                  placeholder="Email"
                  dense
                />
              </v-col>
            </v-row>
          </v-container>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="green darken-1" text @click="dialog=false">キャンセル</v-btn>
            <v-btn color="green darken-1" text @click="regDlg.isOpen=true">登録</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
    <CommonDialog
            :msg="regDlg.msg"
            :is-open="regDlg.isOpen"
            :do-yes="regDlg.doYes"
            :do-no="regDlg.doNo"
    />
  </v-card>
  </div>
</template>

<script>
  import CommonDialog from './CommonDialog.vue';

  export default {
    components: {
        CommonDialog
    },
    data() {
      return {
        dialog: false,
        regDlg: {
          msg: '登録しますか？',
          isOpen: false,
          doYes: ()=>{
            console.log('execute')
            this.regDlg.isOpen=false
            this.dialog=false
          },
          doNo: ()=>{
            this.regDlg.isOpen=false
          },
        },
      }
    },
  }
</script>

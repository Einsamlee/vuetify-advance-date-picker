<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
  <v-container style="padding-top: 0px">
    <v-menu
      ref="menu"
      v-model="menu"
      :close-on-content-click="false"
      offset-y
      lazy
    >
      <template v-slot:activator="{ on }">
        <v-layout>
          <v-text-field
            v-model="date1"
            label="开始日期"
            prepend-icon="event"
            readonly
            v-on="on"
          ></v-text-field>
          <v-text-field
            v-model="date2"
            label="结束日期"
            readonly
            v-on="on"
          ></v-text-field>
        </v-layout>
      </template>
      <v-layout column style="background: white">
          <v-layout row>
          <v-container style="padding-right: 0px;padding-bottom: 0px">
          <v-date-picker
            ref="menu1"
            v-model="date1"
            no-title
            @input="menu1 = false"
            locale="zh-cn"
            class=elevation-0
          ></v-date-picker>
          </v-container>
          <v-container style="padding-bottom: 0px">
          <v-date-picker
            ref="menu2"
            v-model="date2"
            no-title
            :allowed-dates="allowedDates"
            @input="menu2 = false"
            locale="zh-cn"
            class=elevation-0
          >
          </v-date-picker>
          </v-container>
          </v-layout>
        <v-card-text style="background: white;padding-top: 0px;padding-bottom: 10px" class="text-xs-right">
        <v-btn outline  color="primary" @click="cancel">取消</v-btn>
        <v-btn outline  color="primary" @click="save">确认</v-btn>
        </v-card-text>
      </v-layout>
    </v-menu>
  </v-container>
</template>

<script>
  export default {
    name: 'AdvanceDatePicker',
    data() {
      return {
        menu:false,
        date1: '',
        date2: '',
        menu1: false,
        menu2: false,

      };
    },
    methods:{
      cancel(){
        this.menu=false;
        this.date1=this.date2='';
      },
      save(){
        this.menu=false;
        this.date1;
        this.date2;
      },
      allowedDates(date) {
        if (date >= this.date1) {
          return true;
        }
        console.log(date);
      },
    }
  };
</script>

<style scoped>

</style>

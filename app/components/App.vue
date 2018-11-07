<template>
    <Page>
        <ActionBar title="Welcome to NativeScript-Vue!" android:flat="true"/>
                <StackLayout>
                    <TextField hint="datetime" keyboardType="datetime"></TextField>
                    <TextField hint="phone" keyboardType="phone"></TextField>
                    <TextField hint="number" keyboardType="number"></TextField>
                    <TextField hint="url" keyboardType="url"></TextField>
                    <TextField hint="email" keyboardType="email"></TextField>
                    <TextField hint="custDate" @tap="openDatePicker"></TextField>
                    <TextField v-model="date" hint="pluginDatepicker" @tap="openDatePickerPlugin"></TextField>
                </StackLayout>
    </Page>
</template>

<script>
import DatePickerModal from "./DatePickeModal";
import { ModalDatetimepicker } from "nativescript-modal-datetimepicker";

const picker = new ModalDatetimepicker();

export default {
  data() {
    return {
      date: ""
    };
  },
  methods: {
    openDatePicker() {
      this.$showModal(DatePickerModal);
    },
    openDatePickerPlugin() {
      picker
        .pickDate({
          theme: "light",
          maxDate: new Date()
        })
        .then(result => {
          // Note the month is 1-12 (unlike js which is 0-11)
          console.log(
            "Date is: " + result.day + "-" + result.month + "-" + result.year
          );
          var jsdate = new Date(result.year, result.month - 1, result.day);
          var todayUTC = new Date(
            Date.UTC(jsdate.getFullYear(), jsdate.getMonth(), jsdate.getDate())
          );
          this.date = todayUTC.toISOString().slice(0, 10);
        })
        .catch(error => {
          console.log("Error: " + error);
        });
    }
  }
};
</script>

<style scoped>
ActionBar {
  background-color: #53ba82;
  color: #ffffff;
}

.message {
  vertical-align: center;
  text-align: center;
  font-size: 20;
  color: #333333;
}
</style>

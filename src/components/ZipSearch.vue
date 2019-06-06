<template>
  <ion-grid>
    <form @submit="onSubmit">
      <ion-col>
        <ion-item>
          <ion-label>ZipCode:</ion-label>
          <ion-input
            :value="zip"
            @input="zip = $event.target.value"
            name="zip"
            placeholder="Enter US ZipCode"
          />
        </ion-item>
      </ion-col>
      <ion-col>
        <ion-button type="submit" color="primary" expand="block">Find</ion-button>
      </ion-col>
    </form>
  </ion-grid>
</template>

<script>
export default {
  name: "ZipSearch",
  data() {
    return {
      zip: ""
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      const zipRegex = /(^\d{5}$)|(^\d{5}-\d{4}$)/;
      const isValid = zipRegex.test(this.zip);
      if (!isValid) {
        this.showAlert();
      } else {
        this.$emit("get-zip", this.zip);
      }
      this.zip = "";
    },
    showAlert() {
      return this.$ionic.alertController
        .create({
          header: "Enter zipcode",
          message: "Please enter a valid US ZipCode",
          buttons: ["OK"]
        })
        .then(a => a.present());
    }
  }
};
</script>

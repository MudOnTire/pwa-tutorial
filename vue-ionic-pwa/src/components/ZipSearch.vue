<template>
  <ion-grid>
    <form @submit="onSubmit">
      <ion-col>
        <ion-item>
          <ion-label>ZipCode:</ion-label>
          <ion-input :value="zip" @input="zip = $event.target.value" name="zip" placeholder="Enter US ZipCode"/>
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
    onSubmit(e){
      e.preventDefault();
      console.log(this.zip);
    }
  },
};
</script>

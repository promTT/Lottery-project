<template>
  <div class="container">
    <h1 class="alert alert-dark">โปรแกรมทายเลขจากสี</h1>
    <div class="colorinput">
      <label for="exampleColorInput"
        >สีที่ชอบมากที่สุด</label
      >
      <input
        type="color"
        class="form-control form-control-color"
        id="exampleColorInput"
        title="Choose your color"
        v-on:input="myInput"
      />
    </div>
    <ul class="list-group">
      <li class="list-group-item row" :style="{ color }">เลขที่คุณได้คือ: {{ number }}</li>
      <div class="row">
      <li class="list-group-item col" v-for="(item, index) in studentName" :key="index" :style="{ color }">
        {{ item }}
      </li>
      </div>
    </ul>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "crud",
  data() {
    return {
      studentName: ["soon", "coming soon", "coming soon", "coming soon"],
      number: "",
      color: "",
    };
  },
  methods: {
    myInput(event) {
      let hex = event.target.value;
      if (hex != "#ffffff") {
        this.color = hex;
        } else {this.color = "#7a7a7a";}
      hex = hex.replace("#", "");
      let decimal = parseInt(hex, 16);
      decimal = decimal.toString().slice(0, 6);
      if (decimal.length == 6 || decimal == 0) {
        if (decimal == 0) {
          this.number = "ไม่เอาสีดำสิจะหน้าเบื่อไปไหนเนียน???🥱";
        } else {
          this.number = decimal;
        }
      } else {
        this.number = Math.floor(Math.random() * (999999 + 1) );
        console.log("random");
      }

    },
  },
};
</script>

<style scope>
h1 {
  margin-top: 2rem;
}
.colorinput {
  margin-top: 1rem;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
}
.colorinput label {
  margin-right: 1rem;
}
</style>

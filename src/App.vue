<template>
  <div v-for="p in posts.data" :key="p.id">
    <!-- <img :src="p.image_path" :alt="p.name" /> -->
    <h2>{{ p.name }}</h2>
    <p>{{ p.description }}</p>
    <span>R</span>{{ p.price / 100 }}.00
    <!-- <paystack
      buttonClass="'btn btn-primary'"
      buttonText="Buy Now"
      :publicKey="publicKey"
      :email="email"
      :amount="p.price"
      :reference="p.id"
      :onSuccess="onSuccessfulPayment"
      :onCanel="onCancelledPayment"
    >
    </paystack> -->
  </div>
</template>

<script>
//import paystack from 'vue3-paystack';
// import { nanoid } from "nanoid";

export default {
  data() {
    return {
      posts: [],
      // publicKey:'pk_test_c42ffc9fc7bf52355598ad7536490bcaabf72178',
      // amount:1000,
      // email:'chris@smokeyfro.com',
      // firstname='Chris',
      // lastname='Rault'
    };
  },
  components: {
    //paystack,
  },
  computed: {
    // reference: function() {
    //   return nanoid(15);
    // }
  },
  methods: {
    getPosts() {
      fetch('https://api.paystack.co/product', {
        method: 'GET',
        headers: {
          Authorization: `Bearer sk_test_cc0e92417d5ebf47ab7bbb168e57dcec25a12591`,
        },
      })
        .then((response) => response.json())
        .then((data) => (this.posts = data));
    },
    // onSuccessfulPayment: function(response) {
    //   console.log(response);
    // },
    // onCancelledPayment: function() {
    //   console.log("Payment cancelled by user");
    // },
  },
  mounted() {
    this.getPosts();
  },
};
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

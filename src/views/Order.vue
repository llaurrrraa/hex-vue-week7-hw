<template>
  <div class="container">
    <div class="row mt-5 order">
      <div class="col-lg-8 cart-left">
        <div class="title mb-5">
          
          <h6>填寫訂單</h6>
        </div>
        <div class="row">
          <!-- eslint-disable -->
          <!-- <v-form v-slot="{ errors }" @submit="onSubmit" /> -->
          <!-- eslint-disable -->
          <div class="col form-floating mb-3">
            <input
              type="text"
              class="form-control"
              id="floatingInput"
              placeholder="name"
              v-model="form.user.name"
            />
            <label for="floatingInput" class="ms-3">訂購人姓名</label>
          </div>
          <div class="col form-floating">
            <input
              type="text"
              class="form-control"
              id="floatingPassword"
              placeholder="phone"
              v-model="form.user.tel"
            />
            <label for="floatingPassword" class="ms-3">訂購人手機</label>
          </div>
          <div class="col-12 form-floating mb-3">
            <input
              type="text"
              class="form-control"
              id="floatingPassword"
              placeholder="email"
              v-model="form.user.email"
            />
            <label for="floatingPassword" class="ms-3">email</label>
          </div>
          <div class="col-12 form-floating mb-3">
            <input
              type="text"
              class="form-control"
              id="floatingPassword"
              placeholder="address"
              v-model="form.user.address"
            />
            <label for="floatingPassword" class="ms-3">地址</label>
          </div>
          <div class="form-floating">
            <textarea
              class="form-control"
              placeholder="Leave a comment here"
              id="floatingTextarea2"
              style="height: 100px"
              v-model="form.message"
            ></textarea>
            <label for="floatingTextarea2" class="ms-3">想對阿姨說 ..</label>
          </div>
        </div>
        <a href="#/cart">〈&emsp;返回購物車</a>
      </div>
      <div class="col-lg-4 cart-right">
        <div class="title mb-5">
          <h6>訂單資訊</h6>
        </div>
        <div class="card mx-auto" style="width: 20rem">
          <div class="card-body">
            <div class="total_price">
              <p class="card-text">總金額</p>
              <p></p>
            </div>
            <div class="input-group mb-3">
              <input
                type="text"
                class="form-control"
                aria-label="Recipient's username"
                aria-describedby="button-addon2"
              />
              <button
                class="btn btn-outline-secondary"
                type="button"
                id="button-addon2"
              >
                優惠碼
              </button>
            </div>
            <button class="btn d-block w-100 btn-dark" @click="addOrder">
              送出訂單
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      form: {
        user: {
          name: "",
          email: "",
          tel: "",
          address: "",
        },
        message: "",
      },
    };
  },
  methods: {
    addOrder() {
      const api = `${process.env.VUE_APP_URL}v2/api/${process.env.VUE_APP_API_PATH}/order`;
      const order = this.form;
      this.$http
        .post(api, { data: order })
        .then((res) => {
          console.log(res);
        })
        .catch((err) => {
          console.dir(err);
        });
    },
  },
};
</script>

<style lang="scss">
.order {
  .title {
    display: flex;
    justify-content: center;
    h6 {
      margin-bottom: 0;
      letter-spacing: 1.5px;
      color: #9c9c9c;
    }
  }
}
</style>

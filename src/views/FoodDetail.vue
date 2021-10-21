<template>
  <div class="food-detail">
    <Navbar />
    <div class="container">
      <div class="row mt-5">
        <div class="col">
          <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
              <li class="breadcrumb-item">
                <router-link to="/" class="text-dark">Home</router-link>
              </li>
              <li class="breadcrumb-item">
                <router-link to="/foods" class="text-dark">Foods</router-link>
              </li>
              <li class="breadcrumb-item active" aria-current="page">
                Food Order
              </li>
            </ol>
          </nav>
        </div>
      </div>

      <div class="row mt-3">
        <div class="col-md-6">
          <img
            :src="'../assets/images/' + product.gambar"
            alt=""
            class="img-fluid shadow"
          />
        </div>
        <div class="col-md-6">
          <h2>
            <strong>{{ product.nama }}</strong>
          </h2>
          <h4>
            Harga : <strong>Rp. {{ product.harga }}</strong>
          </h4>
          <hr />

          <form action="" class="mt-3" v-on:submit.prevent>
            <div class="form-group">
              <label for="jumlah_pesanan">Jumlah Pesanan</label>
              <input
                type="number"
                class="form-control"
                v-model="pesan.jumlah_pemesanan"
              />
            </div>

            <div class="form-group">
              <label for="keterangan">Keterangan</label>
              <textarea
                v-model="pesan.keterangan"
                class="form-control"
                cols="30"
                rows="5"
                placeholder="Cth: Pedas"
              ></textarea>
            </div>

            <button type="submit" class="btn btn-success" @click="pemesanan">
              <b-icon-cart></b-icon-cart> Pesan
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar.vue";
import axios from "axios";

export default {
  name: "FoodDetail",
  components: {
    Navbar,
  },
  data() {
    return {
      product: {},
      pesan: {},
    };
  },
  methods: {
    setProduct(data) {
      this.product = data;
    },
    pemesanan() {
      if (this.pesan.jumlah_pemesanan) {
        // console.log(this.pesan);
        this.pesan.products = this.product;
        axios
          .post("http://localhost:3000/keranjangs", this.pesan)
          .then(() => {
            //memasukan ke keranjang
            this.$router.push({ path: "/keranjang" });
            // console.log("Berhasil");
            this.$toast.success("Berhasil ditambhakan dikeranjang.", {
              // optional options Object
              type: "success",
              position: "top-right",
            });
          })
          .catch((err) => console.log(err));
      } else {
        this.$toast.error("Jumlah pesanan harus diisi.", {
          // optional options Object
          type: "error",
          position: "top-right",
        });
      }
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/products/" + this.$route.params.id)
      // handle success
      .then((response) => this.setProduct(response.data))
      // handle error
      .catch((error) => console.log("Gagal : ", error));
  },
};
</script>

<style scoped>
.breadcrumb {
  background-color: transparent;
  padding: 0px;
}

.breadcrumb-item.active {
  font-weight: bold;
  color: black;
}

.img-fluid {
  border-radius: 15px;
}
</style>
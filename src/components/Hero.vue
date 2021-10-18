<template>
  <div class="hero">
    <!-- //DESKTOP -->
    <div class="d-none d-md-block">
      <div class="row">
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h2>
                <strong>Delicius Food Menu, </strong> <br />
                in Your Gadget
              </h2>
              <p>Ayo pilih dan pesan makanan favorite Anda</p>
              <router-link to="/foods"
                class="btn btn-lg btn-success"
                style="background-color: #4eb883"
              >
                <b-icon-arrow-right></b-icon-arrow-right> Pesan
              </router-link>
            </div>
          </div>
        </div>
        <div class="col-md-6">
          <img src="../assets/images/ilustrasi.png" alt="" width="100%" />
        </div>
      </div>
    </div>

    <!-- Mobile -->
    <div class="d-md-none d-sm-block">
      <div class="row mt-4">
        <div class="col-md-6 mb-3">
          <img src="../assets/images/ilustrasi.png" alt="" width="100%" />
        </div>
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h2>
                <strong>Delicius Food Menu, </strong> <br />
                in Your Gadget
              </h2>
              <p>Ayo pilih dan pesan makanan favorite Anda</p>
              <button
                class="btn btn-lg btn-success"
                style="background-color: #4eb883"
              >
                <b-icon-arrow-right></b-icon-arrow-right> Pesan
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Hero",
};
</script>
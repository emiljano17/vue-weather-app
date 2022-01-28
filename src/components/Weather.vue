<template>
  <div>
    <div class="row">
      <div class="col-md-6 offset-md-3">
        <div class="card">
          <div class="card-body">
            <img :src="w.icon" :alt="w.status" />
            <p class="text-center">{{ w.status }}</p>
            <h1 class="text-center">{{ w.tempc }} C / {{ w.tempf }} F</h1>
            <p class="text-center">{{ w.lastupdated }}</p>
            <p class="text-center">{{ w.region }}, {{ w.country }}</p>
            <div class="d-flex justify-content-between">
              <p><i class="fa fa-space-shuttle"></i> {{ w.wind }} Mph</p>
              <p><i class="fa fa-tint"></i> {{ w.humidity }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Weather",
  props: ["w"],
};
</script>

<style scoped>
.card {
  margin-bottom: 50px;
}
</style>

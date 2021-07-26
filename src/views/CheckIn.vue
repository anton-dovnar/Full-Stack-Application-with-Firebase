<template>
  <form class="mt-3" @submit.prevent="handleCheckIn">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-lg-6">
          <div class="card bg-light">
            <div class="card-body">
              <h3 class="fw-light mb-3">Check in</h3>
              <section class="mb-3">
                <div class="col-12 alert alert-danger px-3" v-if="error">
                  error
                </div>
                <label
                  class="form-label sr-only"
                  for="displayName"
                >Name</label>
                <input
                  required
                  class="form-control"
                  type="text"
                  placeholder="Name"
                  v-model="displayName"
                />
              </section>
              <section class="mb-3">
                <label
                  class="form-label sr-only"
                  for="Email"
                >Email</label>
                <input
                  required
                  class="form-control"
                  type="email"
                  placeholder="Email"
                  v-model="eMail"
                />
              </section>
              <div class="text-end mb-0">
                <button
                  class="btn btn-primary text-white"
                  type="submit"
                >Check in</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  name: 'checkin',
  data: function () {
    return {
      displayName: null,
      eMail: null
    }
  },
  props: ['error'],
  methods: {
    handleCheckIn: function () {
      this.$emit('checkIn', {
        userID: this.$route.params.userID,
        meetingID: this.$route.params.meetingID,
        displayName: this.displayName,
        eMail: this.eMail
      })
      this.displayName = null
      this.eMail = null
    }
  }
}
</script>

<template>
  <div class="container mt-4">
    <div class="row justify-content-center">
      <div class="col-12 col-md-9 col-lg-7">
        <h1
          class="fw-light text-center"
        >Add a Meeting</h1>

        <div class="card bg-light">
          <div class="card-body text-center">
            <form>
              <div class="input-group input-group-lg">
                <input
                  type="text"
                  class="form-control"
                  name="meetingName"
                  placeholder="Meeting name"
                  aria-describedby="buttonAdd"
                  v-model="meetingName"
                  ref="meetingName"
                />
                <button
                  type="submit"
                  class="btn btn-sm btn-info text-white"
                  id="buttonAdd"
                  @click.prevent="handleAdd"
                >
                  +
                </button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'meetings',
  data: function () {
    return {
      meetingName: null
    }
  },
  methods: {
    handleAdd: function () {
      this.$emit('addMeeting', this.meetingName)
      this.meetingName = null
      this.$refs.meetingName.focus()
    }
  },
  props: ['user']
}
</script>

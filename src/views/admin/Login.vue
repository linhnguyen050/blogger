<template>
  <div class="admin__login">
    <div class="admin__login-main">
      <form novalidate class="md-layout" @submit.prevent="validateUser">
        <md-card class="md-layout-item md-size-100 md-small-size-100">
          <md-card-header>
            <div class="md-title">Sign in with</div>
            <div class="icon">
                <md-icon md-src="/assets/icon-home.svg" />
            </div>
          </md-card-header>

          <md-card-content>
            <div class="md-layout md-gutter">
              <div class="md-layout-item md-small-size-100">
                <md-field>
                  <label for="first-name">First Name</label>
                  <md-input
                    name="first-name"
                    id="first-name"
                    autocomplete="given-name"
                    v-model="form.firstName"
                    :disabled="sending"
                  />
                </md-field>
              </div>

              <div class="md-layout-item md-small-size-100">
                <md-field>
                  <label for="last-name">Last Name</label>
                  <md-input
                    name="last-name"
                    id="last-name"
                    autocomplete="family-name"
                    v-model="form.lastName"
                    :disabled="sending"
                  />
                </md-field>
              </div>
            </div>
          </md-card-content>

          <md-progress-bar md-mode="indeterminate" v-if="sending" />

          <md-card-actions>
            <md-button type="submit" class="md-primary" :disabled="sending"
              >Create user</md-button
            >
          </md-card-actions>
        </md-card>

        <md-snackbar :md-active.sync="userSaved"
          >The user {{ lastUser }} was saved with success!</md-snackbar
        >
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      form: {
        firstName: null,
        lastName: null,
        gender: null,
        age: null,
        email: null
      },
      userSaved: false,
      sending: false,
      lastUser: null
    }
  }
}
</script>

<style lang="scss">
.admin__login {
  align-items: center;
  background-image: url("../../assets/img/register_bg_2.png");
  display: flex;
  justify-content: center;
  background-color: #1A202C;
  min-height: 100vh;

  .admin__login-main {
    min-width: 400px;
  }
}
</style>

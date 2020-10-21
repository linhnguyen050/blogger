<template>
  <div class="admin__login">
    <div class="admin__login-main">
      <form novalidate class="md-layout" @submit.prevent="validateUser">
        <div class="md-title">Sign in with</div>
        <div class="icon">
          <md-button class="md-raised ">Google</md-button>
          <md-button class="md-raised ">Github</md-button>
        </div>
        <div class="md-layout md-gutter">
          <small class="">Or sign in with credentials</small>
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

        <md-progress-bar md-mode="indeterminate" v-if="sending" />

        <md-card-actions>
          <md-button type="submit" class="md-primary" :disabled="sending"
            >Login</md-button
          >
        </md-card-actions>
        <md-snackbar :md-active.sync="userSaved"
          >The user {{ lastUser }} was saved with success!</md-snackbar
        >
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "FontAwesome",
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
    };
  }
};
</script>

<style lang="scss">
.admin__login {
  align-items: center;
  background-image: url("../../assets/img/register_bg_2.png");
  display: flex;
  justify-content: center;
  background-color: #1a202c;
  min-height: 100vh;

  .admin__login-main {
    min-width: 400px;
    background-color: #e2e8f0;
    .md-layout {
      display: block;
      margin: 30px 0px;
      small {
        font-size: 17px;
        color: #777;
        font-weight: 900;
        padding: 80px;
      }

      .md-title {
        display: flex;
        justify-content: center;
        margin: 40px 0px 5px;
        font-weight: 700;
        color: rgb(113, 128, 150);
        font-size: 14px;
        line-height: 21px;
      }
      .icon {
        display: flex;
        justify-content: center;
        border-bottom: 1px solid #a2aebd;
        button {
          margin: 10px 10px 50px 10px;
          background-color: #ffffff;
        }
        .md-ripple {
          background-color: #ffffff;
        }
        .md-button-content {
          color: rgb(113, 128, 150);
          font-weight: 700;
        }
      }
    }
    .md-card-actions.md-alignment-right {
      justify-content: center;
      .md-button {
        width: 300px;
        font-weight: 900;
        margin: 22px 0px;
        .md-ripple {
          background-color: black;
        }
      }
    }
  }
}
</style>

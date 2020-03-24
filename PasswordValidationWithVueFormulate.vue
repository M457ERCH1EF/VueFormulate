<template>
    <div>
        <span>* Password must be more than 8 characters long, contain at least 1 uppercase and 1 number character</span>
        <FormulateForm
            v-model="formValues"
            @submit="submitHandler"
        >
            <FormulateInput
                name="password"
                type="password"
                label="New Password"
                :validation="[['matches', /^(?=.*[A-Z])(?=.*[0-9])(?=.{8,})/]]"
                validation-name="New Password"
                error-behavior="live"
            />
            <FormulateInput
                name="password_confirm"
                type="password"
                label="Confirm Password"
                validation="required|confirm" 
                validation-name="Confirm Password"
            />
            <FormulateInput
                type="submit"
                label="Submit"
            />
            <FormulateInput
                type="button"
                label="Reset"
                v-on:click.native="resetform()"
            />
        </FormulateForm>
    </div>
</template>

<script>
import '../node_modules/@braid/vue-formulate/themes/snow/snow.scss';
import Vue from "vue";
import VueFormulate from '@braid/vue-formulate';

Vue.use(VueFormulate);

export default {
    data () {
        return {
            formValues: {},
        }
    },
    methods: {
      submitHandler (data) {
        console.log(`Your Password, ${data.password}`)
      },
      resetform () {
        this.formValues= {
          password: '',
          password_confirm: ''
        }
      },
    }
}
</script>

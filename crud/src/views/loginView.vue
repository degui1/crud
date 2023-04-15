<template>
    <v-container fill-height>
    <v-row justify="center">
        <v-col cols="6">
            <v-row>
                <v-col class="text-center">
                    <v-sheet class="pa-2 text-h4">
                    Login
                    </v-sheet>
                </v-col>
            </v-row>
            <v-row>
                <v-col>
                    <v-form ref="form" class="">
                    <v-text-field
                    v-model="userData.email"
                    :rules="[rules.required, rules.email]"
                    label="E-mail:"
                    required
                    outlined
                    dense
                    ></v-text-field>

                    <v-text-field
                    v-model="userData.password"
                    :rules="[rules.required]"
                    label="Senha:"
                    required
                    outlined
                    dense
                    ></v-text-field>

                    <div class="d-flex flex-column">
                    <v-btn
                        color="primary"
                        class="mt-4"
                        block
                        @click="validate"
                    >
                        Entrar
                    </v-btn>

                    </div>
                    </v-form>
                </v-col>
            </v-row>
        </v-col>
    </v-row>
  </v-container>
</template>
<script>
export default {
    name: 'RegisterVue',

    data(){
        return {
            valid: true,
            userData: {
                email: '',
                password: '',
            },
            rules: {
                required: value => !!value || 'Campo obrigatório',
                email: value => {
                    const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
                    return pattern.test(value) || 'E-mail inválido.'
                },
            },
        }
    },

    methods: {
        validate () {
          console.log(this.userData)
        },
    },
}
</script>
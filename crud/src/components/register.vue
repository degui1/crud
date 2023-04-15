<template>
  <v-container fill-height>
    <v-row no-gutters justify="center">
      <v-col cols="6">
        <v-row>
          <v-col class="text-center">
            <v-sheet class="pa-2 text-h4">
              Cadastrar
            </v-sheet>
          </v-col>
        </v-row>
        <v-row>
          <v-col>
            <v-form ref="form">
              <v-text-field
                v-model="name"
                :counter="10"
                :rules="[rules.required]"
                label="Nome:"
                required
                outlined
                dense
              ></v-text-field>
        
              <v-text-field
                v-model="last_name"
                :counter="10"
                :rules="[rules.required]"
                label="Sobrenome:"
                required
                outlined
                dense
              ></v-text-field>
        
              <v-text-field
                v-model="email"
                :rules="[rules.required, rules.email]"
                label="E-mail:"
                required
                outlined
                dense
              ></v-text-field>
        
              <v-select
                v-model="select"
                :items="items"
                :rules="[rules.required]"
                label="Sexo"
                required
                outlined
                dense
              ></v-select>
        
              <v-checkbox
                v-model="checkbox"
                :rules="[v => !!v || 'You must agree to continue!']"
                label="Você concorda ?"
                required
              ></v-checkbox>
        
              <div class="d-flex flex-column">
                <v-btn
                  color="success"
                  class="mt-4"
                  block
                  @click="validate"
                >
                  Validar
                </v-btn>
        
                <v-btn
                  color="error"
                  class="mt-4"
                  block
                  @click="reset"
                >
                  Limpar formulário
                </v-btn>
        
              </div>
            </v-form>
          </v-col>
        </v-row>
      </v-col>
    </v-row>
    <!-- <v-sheet width="600" class="mx-auto"> -->
    <!-- </v-sheet> -->
  </v-container>
</template>


<script>
import { crud } from '@/crud/crud.js';
  export default {
    name: 'RegisterVue',

    data: () => ({
      valid: true,
      name: '',
      last_name: '',
      email: '',
      
      select: null,
      items: [
        'Masculino',
        'Feminino',
        'Não informar'
      ],
      checkbox: false,
      rules: {
          required: value => !!value || 'Campo obrigatório',
          email: value => {
            const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/
            return pattern.test(value) || 'E-mail inválido.'
          },
      },
    }),

    methods: {
      async validate () {
        const { valid } = await this.$refs.form.validate()

        if (valid) {
          console.log(crud)
        }
      },
      reset () {
        this.$refs.form.reset()
      },
    },
  }
</script>

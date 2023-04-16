<template>
  <v-container fill-height>
    <v-row justify="center">
      <v-col cols="10">
        <v-snackbar
        v-model="snackbar"
        :timeout="timeout"
        shaped
        absolute
        color="green"
    >
        {{snackbarText}}
    </v-snackbar>
    <v-data-table
      :headers="headers"
      :items="desserts"
      :page.sync="page"
      :items-per-page="itemsPerPage"
      hide-default-footer
      class="elevation-1"
      @page-count="pageCount = $event"
    >
      <template v-slot:top>
        <v-toolbar flat>
          <v-toolbar-title>Gestão de usuários</v-toolbar-title>
          <v-divider class="mx-4" inset vertical></v-divider> 
        </v-toolbar>
        <v-dialog v-model="dialogDeleteUser" persistent max-width="900">
          <v-card>
            <v-card-text>
              <v-container>
                <v-row justify="center">
                  <v-col class="text-center">
                    Deseja excluir o usuário?
                  </v-col>
                </v-row>
                <v-spacer></v-spacer>
                <v-divider inset></v-divider>
                <v-row justify="end" class="mr-3 mt-1">
                  <v-col xs="6" sm="2" md="2" xl="1" class="text-right">
                    <v-btn
                      color="actionButton"
                      depressed
                      small
                      @click="closeDialog"
                    >
                      Cancelar
                    </v-btn>
                  </v-col>
                  <v-col xs="6" sm="2" md="1" xl="1" class="text-right">
                    <v-btn
                      color="red"
                      depressed
                      small
                      @click="deleteUser(exibe)"
                    >
                      Excluir
                    </v-btn>
                  </v-col>
                </v-row>
              </v-container>
            </v-card-text>
          </v-card>
        </v-dialog>
      </template>
      <!-- Nesse slot ficam os ícones de ações -->
      <template v-slot:[`item.config`]="{ item }">
        <v-icon class="red--text mx-2" @click="deleteUser(item)">
          mdi-delete
        </v-icon>
      </template>
    </v-data-table>
    <div class="text-center pt-2">
      <v-pagination
        v-model="page"
        :length="pageCount"
        color="actionButton"
      ></v-pagination>
    </div>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
export default {
  name: 'userView',
  data(){
    return {
      dialogDeleteUser: false,
      headers: [
        { text: "Nome", align: "start", value: "name" },
        { text: "Sobrenome", value: "last_name" },
        { text: "E-mail", value: "email" },
        { text: "Ações", value: "config", sortable: false },
      ],
      desserts: [
          {
            name: 'Guilherme',
            last_name: 'Denez',
            email: 'gui.@gmail.com',
          },
          {
            name: 'Guilherme',
            last_name: 'Denez',
            email: 'gui.@gmail.com',
          },
          {
            name: 'Guilherme',
            last_name: 'Denez',
            email: 'gui.@gmail.com',
          },
          {
            name: 'Guilherme',
            last_name: 'Denez',
            email: 'gui.@gmail.com',
          },
          {
            name: 'Guilherme',
            last_name: 'Denez',
            email: 'gui.@gmail.com',
          },
          {
            name: 'Guilherme',
            last_name: 'Denez',
            email: 'gui.@gmail.com',
          },
          {
            name: 'Lucas',
            last_name: 'Santos',
            email: 'gui.@gmail.com',
          },
          {
            name: 'João',
            last_name: 'Pessoa',
            email: 'gui.@gmail.com',
          },
        ],
        snackbar: false,
      snackbarText: 'Atualizado!',
      timeout: 5000,
      expanded: [],
      selected: [],
      page: 1,
      users: [],
      pageCount: 0,
      itemsPerPage: 10,
      updatedUser: {
        name: "",
        email: "",
        status: "",
        accessLevel: "",
      },
      search: "",
    }
  },
  methods: {
    deleteUser() {
      this.dialogDeleteUser=true
    },
    closeDialog() {
      this.dialogDeleteUser = false;
    },
  },
}
</script>
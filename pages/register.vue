<template>
  <v-card class="mx-auto" max-width="500">
    <v-card-title class="justify-center">
      <div>Registracija</div>
    </v-card-title>
  
   
    <v-form ref="regForm" v-model="valid">
        <v-row justify="center">
            <v-col cols="12" sm="10" md="8" lg="8">
                <v-text-field
                    v-model="ime"
                    :rules="imeRules"
                    label="Ime"
                    @keyup.enter="submitReg"
                    required
                ></v-text-field>
                <v-text-field
                    v-model="prezime"
                    :rules="prezimeRules"
                    label="Prezime"
                    @keyup.enter="submitReg"
                    required
                ></v-text-field>
                <v-text-field
                    v-model="email"
                    :rules="emailRules"
                    label="E-mail"
                    @keyup.enter="submitReg"
                    required
                ></v-text-field>
                <v-text-field
                    v-model="lozinka"
                    :append-icon="show1 ? 'mdi-eye' : 'mdi-eye-off'"
                    :rules="lozinkaRules"
                    :type="show1 ? 'text' : 'password'"
                    label="Lozinka"
                    counter
                    @keyup.enter="submitReg"
                    required
                    @click:append="show1 = !show1"
                ></v-text-field>
                <div class="text-center">
                    <v-btn class="ma-2" 
                    outlined 
                    color="indigo" 
                    dark large
                    @click="submitReg">
                    Registriraj se
                    </v-btn>
                </div>  
             </v-col>
        </v-row>
    </v-form>
  </v-card>
</template>


<script>
  export default {
    data: () => ({
      valid: true,
      ime: '',
      imeRules: [
        v => !!v || 'Obavezno polje!',
      ],
      prezime: '',
      prezimeRules: [
        v => !!v || 'Obavezno polje!',
      ],
      email: '',
      emailRules: [
        
        v => /.+@.+\..+/.test(v) || 'E-mail mora biti validan!',
      ],
      lozinka: '',
        show1: false,
        show2: true,
      lozinkaRules: [
        v => !!v || 'Obavezno polje!',
        v => v.length >= 8 || 'Najmanje 8 znakova',
      ],
    }),

  methods: {
      submitReg(evt) {
        evt.preventDefault()
        console.log("TEST")
        const userInfo = {
          ime: this.ime,
          prezime: this.prezime,
          email: this.email
        }
        alert(JSON.stringify(userInfo))
      },
    }
  }
</script>

<style>
</style>
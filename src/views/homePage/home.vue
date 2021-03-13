<template>
  <v-row justify="center" align="center" no-gutters class="homepage">
      <v-col 
        cols="12" 
        sm="10" 
        md="8" 
        lg="4" 
        xl="2"
      >
        <v-row justify="center">
            <v-col cols="12">
              <v-img 
                src="@/assets/logo.svg" 
                contain 
                max-height="100"
              />
            </v-col>
            <v-col md="10">
              <v-text-field
                class="inputCustom"
                solo
                hide-details
                placeholder="Copacabana"
                style="font-size: 1.3rem !important;"
              >
                <template v-slot:prepend-inner>
                    <v-icon size="35" class="mr-2 ml-2">
                        mdi-magnify
                    </v-icon>
                </template>
              </v-text-field>
            </v-col>
        </v-row>
      </v-col>
  </v-row>
</template>

<script>
export default {

}
</script>

<style lang="sass">
.homepage
 .inputCustom > 
  .v-input__control > 
   .v-input__slot 
    height: 67px !important
</style>
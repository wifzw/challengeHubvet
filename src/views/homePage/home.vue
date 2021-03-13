<template>
  <v-row justify="center" align="center" no-gutters class="homepage">
      <v-col 
        cols="12" 
        sm="10" 
        md="8" 
        xl="4"
      >
        <v-row justify="center">
            <v-col cols="12">
              <v-img 
                src="@/assets/logo.svg" 
                contain 
                max-height="100"
              />
            </v-col>
            <v-col md="6">
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
            <v-col cols="12" class="mt-2">
             <v-row>
                <v-col class="flex-shrink-1 flex-grow-1 mr-2">
                 <v-select
                   v-model="modelPackets"
                   :items="itemsPackets"
                   label="Buscar por"
                 />
                </v-col>   
                 <v-col class="flex-shrink-1 flex-grow-1 mr-2">
                  <v-select
                   v-model="modelCity"
                   :items="itemsCity"
                   label="Onde você está?"
                  />
                </v-col>
                <v-col class="flex-shrink-1 flex-grow-1 d-flex align-center">
                    <v-row no-gutters>
                        <v-col cols="12" class="d-flex justify-center ml-md-5">
                         <v-btn 
                           v-model="milesAndBrl.modelMiles"
                           outlined 
                           :color="milesAndBrl.modelBrl === true ? 'secondary' : 'primary'"
                           @click="changeMilles(milesAndBrl)"
                          >                    
                          <v-icon 
                            :color="milesAndBrl.modelBrl === true ? 'secondary' : 'primary'"
                          >
                             mdi-circle-multiple-outline
                          </v-icon>
                          </v-btn>
                          <v-btn 
                            v-model="milesAndBrl.modelBrl"
                            outlined 
                            :color="milesAndBrl.modelBrl === true ? 'primary' : 'secondary'"
                            @click="changeMilles(milesAndBrl)"
                          >
                            <v-icon  :color="milesAndBrl.modelBrl === true ? 'primary' : 'secondary'">
                                mdi-currency-usd
                            </v-icon>
                          </v-btn>    
                        </v-col>
                    </v-row>
                </v-col>
                <v-col md="5" class="ml-4 ">
                <!-- :search-input.sync="search" -->
                 <v-combobox
                   v-model="model"
                   :items="itemsDemo"
                   hide-selected
                   label="Etiquetas"
                   multiple
                   persistent-hint
                   small-chips
                 >
                 <template v-slot:selection="data">
                <v-chip
                  color="error"
                  outlined
                  v-bind="data.attrs"
                  :input-value="data.selected"
                  @click:close="data.parent.selectItem(data.item)"
                >
                 {{ data.item }}
                </v-chip>
                 </template>
               </v-combobox>
              </v-col>   
             </v-row>
            </v-col>
            <v-col 
              cols="12" 
              class="d-flex justify-center"
             >
              <v-btn
                color="primary"
                tile
                width="185"
                height="38"
              >
                Pesquisar
              </v-btn>
            </v-col>
        </v-row>
      </v-col>
  </v-row>
</template>

<script>
export default {

 data: () => ({
    itemsDemo: [
     'Promoção', 
     'Novos', 
     'Últimos dias'
    ],
    itemsPackets: [
        'Pacotes'
    ],
    modelPackets: null,
    modelCity: null,
    modelMilhas: null,
    itemsCity: [
        'São Paulo',
        'Lages',
        'Blumenau'
    ],
    milesAndBrl: {
        modelBrl: false,
        modelMiles: true
    },
    model: null
 }),
 methods: {
     changeMilles(item) {
         if(item.modelBrl) {
             this.milesAndBrl.modelBrl = !this.milesAndBrl.modelBrl
             this.milesAndBrl.modelMiles = !this.milesAndBrl.modelMiles
         } else {
             this.milesAndBrl.modelBrl = !this.milesAndBrl.modelBrl
             this.milesAndBrl.modelMiles = !this.milesAndBrl.modelMiles
         }
     }
 }
}
</script>

<style lang="sass">
.homepage
 .inputCustom > 
  .v-input__control > 
   .v-input__slot 
    height: 67px !important
</style>
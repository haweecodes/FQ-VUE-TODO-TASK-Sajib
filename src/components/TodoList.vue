<template>
  <div>
    <v-container>
      <v-layout wrap row class="container-card">
        <v-flex xs6 offset-xs3>
          <v-card class="mx-auto">
            <v-card-title>My To Do List</v-card-title>
            <v-card-text>
              <div class="list-container">
                <v-list-item>
                  <v-list-item-content>
                    <v-list-item-title v-for="(item, i) in itemList" :key="i"> 
                        Single-line item
                    </v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </div>
            </v-card-text>
            <v-card-actions>
              <v-text-field outlined v-model="item"></v-text-field>
            </v-card-actions>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>
<script>
export default {
    data(){
        return{
            item: "",
            itemList: []
        }
    }
}
</script>

<style>
.container-card {
  margin: 30px 0px;
}
.list-container {
  max-height: 100%;
  overflow-y: auto;
}
</style>
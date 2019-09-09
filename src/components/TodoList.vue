<template>
  <div>
    <v-container>
      <v-layout wrap row class="container-card">
        <v-flex xs6 offset-xs3>
          <v-card class="mx-auto">
            <v-card-title>My To Do List</v-card-title>
            <v-card-actions>
              <v-text-field
                placeholder="Press enter to add"
                v-model="item"
                @keyup.enter="addItem()"
              ></v-text-field>
            </v-card-actions>
            <v-card-text>
              <div class="list-container">
                <v-list-item>
                  <v-list-item-content v-if="itemList.length != 0">
                    <v-list-item-title v-for="(item, i) in itemList" :key="i">
                      <div class="list-items">
                        <v-layout>
                          <v-flex xs10>
                            <p id="item">{{item}}</p>
                          </v-flex>
                          <v-flex xs2>
                            <v-btn icon color="blue" @click="edit(i)">
                              <v-icon>edit</v-icon>
                            </v-btn>
                            <v-btn icon class="red" @click="remove(i)">
                              <v-icon>close</v-icon>
                            </v-btn>
                          </v-flex>
                        </v-layout>
                      </div>
                    </v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </div>
            </v-card-text>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>
<script>
export default {
  data() {
    return {
      item: "",
      itemList: [],
      isEdit: false,
      id: 0
    };
  },
  beforeMount(){
      let items= JSON.parse(localStorage.getItem('list'));
      if(items.length > 0 ){
          this.itemList = [... items]
      }
  },
  updated() {
    localStorage.setItem("list", JSON.stringify(this.itemList));
  },
  methods: {
    addItem() {
      if (this.item != "") {
        if (!this.isEdit) {
          this.itemList.push(this.item);
          this.item = "";
        } else {
          this.itemList[this.id] = this.item;
          this.item = "";
        }
      }
    },
    edit(index) {
      this.isEdit = true;
      this.item = this.itemList[index];
      this.id = index;
    },
    remove(index) {
      this.itemList.splice(index, 1);
    }
  }
};
</script>

<style>
.container-card {
  margin: 30px 0px;
}
.list-container {
  max-height: 300px;
  overflow-y: auto;
}
.list-items {
  font-size: 18px;
  margin: 10px;
}
.list-items .item {
  word-break: break-all;
}
</style>
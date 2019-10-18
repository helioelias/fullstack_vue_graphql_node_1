<template>
  <div>    
    <h5>{{ title }} <span class="badge badge-info">{{ items.length }}</span></h5>
    <div class="card">
      <div class="card-body">
        <ul class="list-group">
          <li class="list-group-item" v-for="item in items" v-bind:key="item">
            <div class="row">
              <div class="col-md">
                {{ item }}
              </div>
              <div class="col-md text-right">
                <button class="btn btn-info" v-on:click="deleteItem(item)"><span class="fa fa-trash"></span></button>
              </div>
            </div>
          </li>
        </ul>
        <br />
        <div class="input-group">
          <input v-model="item" type="text" class="form-control" v-on:keyup.enter="additem(item)" placeholder="Digite o item" />
          <div class="input-group-">
            <button class="btn btn-info" v-on:click="addItem(item)"><span class="fa fa-plus"></span></button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
	name: "AppItemList",
	props: ["title", "items"],
	data() {
		return {
			item: ""
		};
	},
	methods: {
		addItem(item) {
			this.$emit("addItem", item);
			this.item = "";
		},
		deleteItem (item) {
			this.$emit("deleteItem", item);
			this.items.splice(this.items.indexOf(item), 1);
		}
	}
};
</script>

<style scoped>
</style>

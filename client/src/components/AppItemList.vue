<template>
  <div>    
    <h5>{{ title }} <span class="badge badge-info">{{ items.length }}</span></h5>
    <div class="card">
      <div class="card-body">
        <ul class="list-group">
          <li class="list-group-item" v-for="item in items" v-bind:key="item.id">
            <div class="row">
              <div class="col-md">
                {{ item.description }}
              </div>
              <div class="col-md text-right">
                <button class="btn btn-info" v-on:click="deleteItem(item)"><span class="fa fa-trash"></span></button>
              </div>
            </div>
          </li>
        </ul>
        <br />
        <div class="input-group">
          <input v-model="description" type="text" class="form-control" v-on:keyup.enter="additem(type, description)" placeholder="Digite o item" />
          <div class="input-group-">
            <button class="btn btn-info" v-on:click="addItem(type, description)"><span class="fa fa-plus"></span></button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
	name: "AppItemList",
	props: ["title", "type", "items"],
	data() {
		return {
			description: ""
		};
	},
	methods: {
		addItem(type, description) {
			this.$emit("addItem", {
				type,
				description
			});
			this.description = "";
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

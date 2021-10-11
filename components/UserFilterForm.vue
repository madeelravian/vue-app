<template>
<div class="row">
<div class="col-6">
<form class="d-flex">
        <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search" v-model="keyword">
        <button class="btn btn-outline-success" type="button" @click="searchUser">Search</button>
</form>

</div>
	<div class="col-2">
		<NuxtLink to="/user/add" class="btn btn-primary">Add User</NuxtLink>
	</div>
	<div class="col-4 d-flex justify-content-end">
		<div class="sort_container"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" class="sort_icon"><path d="M6 21l6-8h-4v-10h-4v10h-4l6 8zm16-12h-8v-2h8v2zm2-6h-10v2h10v-2zm-4 8h-6v2h6v-2zm-2 4h-4v2h4v-2zm-2 4h-2v2h2v-2z"></path></svg> 
		<select v-model="sortType" @change="sortUsers()" name="sort_by" class="form-control">
                                    <option value="">Sort</option>
                                    <option value="asc">Asc</option>
                                    <option value="desc">Desc</option>
                                </select>
		</div>
	</div>
</div>

</template>

<style>
.sort_container {
    position: relative;
    display: flex;
    align-items: center;
    width:100px;
}
.sort_container .sort_icon {
    position: absolute;
    left: 7px;
}
.sort_container select[name='sort_by'] {
    text-indent: 20px;
}
</style>

<script>
export default{
		data(){
			return {
					keyword:'',
					btn_pressed:false,
					sortType:''
			}
		},
		methods: {
		    searchUser() {
		    	//this.btn_pressed=true;
		      	this.$parent.searchUser(this.keyword);
		    },
		    sortUsers(){
		    	this.$parent.sortUsers(this.sortType);
		    	//alert(this.sortType);
		    }
  		}
}
</script>


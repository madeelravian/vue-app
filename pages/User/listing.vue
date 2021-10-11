<template>
<div>
  <Header/>
  <main role="main" class="container mt-4">
  <h1 class="mt-3 underline">Users</h1>
      <UserFilterForm />
<div v-if="keyword" class="mt-4">
	Result For <strong>{{keyword}}</strong>
</div>
							<!--Loader-->
                            <div class="d-flex justify-content-center" v-if="showLoader" style="height: 50vh; align-items: center;">
                                <div class="spinner-border" role="status">
                                    <span class="sr-only"></span>
                                </div>
                            </div>
                            <!--Loader-->
      <div class="row mt-4" v-if="!showLoader">
      	<UserCard v-for="(user, index) in results" :key="index" :user=user />
      </div>

      <div class="row mt-4" v-if="!results.length && !showLoader">
      	No Record Found.
      </div>


  </main>
  <Pagination v-if="!showLoader" :currentPage=currentPage :total_pages=total_pages />
</div>
</template>

<script>
export default {

data() {
                        return {
                        	keyword:'',
                            results: [],
                            sortType: '',
                            total_records:'',
                            projectStatus:'',
                            showLoader:true,
                            currentPage:1,
                            total_pages:'',
                        }
                    },
	async fetch(){
		this.getUsers();
	},
	methods: {
    searchUser(keyword) {
        this.currentPage=1;
      this.keyword=keyword;
      this.getUsers();
    },
    getUsers(){
    		this.showLoader=true;
			fetch("https://dev.athr.ae/api/get-users", {
                                method: 'POST',
                                headers: {
                                    'Content-Type': 'application/json',
                                },
                                body: JSON.stringify({
                                    "sort_type": this.sortType,
                                    "page":this.currentPage,
                                    "keyword":this.keyword
                                })
                            }).then(res => {
                                if (!res.ok) {
                                    // create error instance with HTTP status text
                                    const error = new Error(res.statusText);
                                    error.json = res.json();
                                    throw error;
                                }
                                return res.json();
                            }).then(json => {
                                    console.log(json);
                                    window.scrollTo(0,0);
                                    this.results = JSON.parse(json.results);
                                    this.total_records=json.total_records;
                                    this.total_pages=json.total_pages;
                                })
                                .catch(err => {
                                    console.log("ERROR");
                                })
                                .then(() => {
                                    console.log("Always");
                                    this.showLoader=false;
                                    //loading.value = false;
                                });
    },
    paginate(page_no){
    	this.currentPage = page_no;
    	this.getUsers();
    },
    sortUsers(sortType){
    		this.sortType = sortType;
    		this.currentPage=1;
    		this.getUsers();
    }
  }
}

</script>

<style>
.underline{
	    position: relative;
    line-height: 50px;
}
.underline::after{
	    content: '';
    position: absolute;
    width: 10%;
    width: 90px;
    border-bottom: 2px solid #cee9f1;
    left: 5px;
    bottom: -2px;
}
</style>
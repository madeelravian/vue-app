<template>
<div class="col-12 col-sm-4 mb-3">
	<div class="card pt-4">
	<div class="rounded-circle user_img"><img class="card-img-top z-depth-2" alt="100x100" :src="user.user_profile_image"></div>
	  <div class="card-body">
	    <h5 class="card-title">{{user.first_name}} {{user.last_name}}</h5>
	    <p class="card-text">
	    	<div><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"><path d="M0 3v18h24v-18h-24zm6.623 7.929l-4.623 5.712v-9.458l4.623 3.746zm-4.141-5.929h19.035l-9.517 7.713-9.518-7.713zm5.694 7.188l3.824 3.099 3.83-3.104 5.612 6.817h-18.779l5.513-6.812zm9.208-1.264l4.616-3.741v9.348l-4.616-5.607z"/></svg>
			{{user.email}}
	    	</div>
	    </p>
	    <a href="#" class="btn btn-primary">Go somewhere</a>
	  </div>
	</div>
</div>	
</template>

<script>
export default {
	props: ['user']
}
</script>

<style>
.user_img{
	width:180px;
	height:180px;
	margin:0 auto;
	overflow:hidden;
}

.user_img img{
	width:100%;
}

.card{
	transition: .5s;
}
.card:hover{
	box-shadow: 0 0 10px 0 rgb(0 0 0);
}
</style>
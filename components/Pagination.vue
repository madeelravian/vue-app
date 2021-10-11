<template>
<nav class="mb-3 mt-2" v-if="total_pages">
<ul class="pagination">
<li class="page-item" :class="{disabled: currentPage==1}" v-on="currentPage!=1 ? { click: () => paginate(currentPage-1) } : {}">
                                                <a class="page-link" href="#" aria-label="Previous">
                                                    <span aria-hidden="true">&laquo;</span>
                                                </a>
                                            </li>
                                            <li class="page-item" :class="{ active: page_number==currentPage }" v-for="page_number in total_pages" v-on="page_number!=currentPage ? { click: () => paginate(page_number) } : {}"><a class="page-link" href="javascript:">{{ page_number }}</a></li>
                                            <li class="page-item" :class="{disabled: currentPage==total_pages}" v-on="currentPage!=total_pages ? { click: () => paginate(currentPage+1) } : {}">
                                                <a class="page-link" href="#" aria-label="Next">
                                                    <span aria-hidden="true">&raquo;</span>
                                                </a>
                                            </li>
                                        </ul></nav>
</template>

<style>
.pagination {
    justify-content: center;
    overflow: auto;
}
</style>

<script>
export default{
	props: ['currentPage','total_pages'],
	data(){
			return {
					page_no_test:'',
					results:this.results
			}
		},
	methods: {
		    paginate(page_no) {
		    		//this.$parent.showLoader=true;
		    		this.$parent.paginate(page_no);
		    		//window.scrollTo({ top: 0 });
		    }
  		}
}
</script>
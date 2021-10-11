<template>
<div>
  <Header/>
  <main role="main" class="container mt-4">
      <div class="starter-template">
        <h1>Welcome</h1>
        <p class="lead">Please go to user page to view the users.</p>
      </div>
    </main>
</div>  
</template>

<script>
export default {
 created() {
    this.$router.push('/user/listing')
  },
}
</script>

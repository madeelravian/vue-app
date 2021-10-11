<template>
<nav class="navbar navbar-expand-lg navbar-dark bg-dark">
  <div class="container">
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav me-auto mb-2 mb-lg-0">
        <li class="nav-item">
        <NuxtLink to="/" class="nav-link">Home</NuxtLink>
        </li>
        <li class="nav-item">
          <NuxtLink to="/user/listing" class="nav-link">Users</NuxtLink>
        </li>
      </ul>
    </div>
  </div>
</nav>
</template>

<style>
.nuxt-logo {
  height:
  }

.navbar-dark .navbar-nav .nav-link{
  color:white;
  text-transform:uppercase;
}
  .nuxt-link-exact-active{

   box-shadow: inset 1px 6px 12px #7c59a5, inset -1px -10px 5px #3f245f, 1px 2px 1px black;
   background-color: #3f245f;
   border-radius:3px;

  }
</style>

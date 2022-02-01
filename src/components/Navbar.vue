<template>
<nav class="navbar d-print navbar-expand-lg navbar-light bg-info">
  <a class="navbar-brand" href="#">
      <img src="@/assets/faircorp.png" width="70" height="30" alt="faircorp logo">
  </a>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>
  <div class="collapse navbar-collapse" id="navbarNav">
    <ul class="navbar-nav">
      <li class="nav-item active">
        <a class="nav-link" href="/">Home</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="/windows-list">Window List</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="/rooms-list">Room List</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="/contact">Contact us</a>
      </li>
    </ul>
  </div>
</nav>
</template>

<style scoped>
a.navbar-brand img {
    padding-left: 10px;
}
</style>
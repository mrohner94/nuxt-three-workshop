<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <a class="navbar-item" href="https://bulma.io"> MyRecs </a>

      <a
        role="button"
        class="navbar-burger"
        aria-label="menu"
        aria-expanded="false"
        data-target="navbarBasicExample"
      >
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
        <span aria-hidden="true"></span>
      </a>
    </div>

    <div id="navbarBasicExample" class="navbar-menu">
      <div class="navbar-start"></div>

      <div class="navbar-end mr-6">
        <NuxtLink to="/" class="navbar-item"> Home </NuxtLink>

        <div class="navbar-item has-dropdown is-hoverable mx-6">
          <NuxtLink to="/display" class="navbar-item"> Display </NuxtLink>

          <div class="navbar-dropdown">
            <NuxtLink to="/display/todos" class="navbar-item">
              To-Do's
            </NuxtLink>
            <NuxtLink to="/display/todos?completed=true" class="navbar-item">
              Completed To-Do's
            </NuxtLink>
            <NuxtLink to="/display/photos" class="navbar-item">
              Photos
            </NuxtLink>
            <hr class="navbar-divider" />
            <a class="navbar-item"> Report an issue </a>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

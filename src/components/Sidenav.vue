<template>
<div class="col-1">
    <nav id="sidebar" class="col sidebar">
      <a class="navbar-brand" href="#">
        <img src="../assets/logo.png" alt="logo" class="logo" />
      </a>
      <ul class="nav flex-column">
        <li class="nav-item">
          <router-link :to="{ name: 'Dashboard' }" :class="$route.name === 'Dashboard' ? 'nav-link active' : 'nav-link'">
             <svg width="1em" height="1em" viewBox="0 0 16 16" class="bi bi-bar-chart-line-fill" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
              <rect width="4" height="5" x="1" y="10" rx="1"/>
              <rect width="4" height="9" x="6" y="6" rx="1"/>
              <rect width="4" height="14" x="11" y="1" rx="1"/>
              <path fill-rule="evenodd" d="M0 14.5a.5.5 0 0 1 .5-.5h15a.5.5 0 0 1 0 1H.5a.5.5 0 0 1-.5-.5z"/>
            </svg>
          </router-link>
        </li>
        <li class="nav-item">
          <router-link :to="{ name: 'User' }" :class="$route.name === 'User' ? 'nav-link active' : 'nav-link'">
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-card-checklist" viewBox="0 0 16 16">
              <path d="M14.5 3a.5.5 0 0 1 .5.5v9a.5.5 0 0 1-.5.5h-13a.5.5 0 0 1-.5-.5v-9a.5.5 0 0 1 .5-.5h13zm-13-1A1.5 1.5 0 0 0 0 3.5v9A1.5 1.5 0 0 0 1.5 14h13a1.5 1.5 0 0 0 1.5-1.5v-9A1.5 1.5 0 0 0 14.5 2h-13z"/>
              <path d="M7 5.5a.5.5 0 0 1 .5-.5h5a.5.5 0 0 1 0 1h-5a.5.5 0 0 1-.5-.5zm-1.496-.854a.5.5 0 0 1 0 .708l-1.5 1.5a.5.5 0 0 1-.708 0l-.5-.5a.5.5 0 1 1 .708-.708l.146.147 1.146-1.147a.5.5 0 0 1 .708 0zM7 9.5a.5.5 0 0 1 .5-.5h5a.5.5 0 0 1 0 1h-5a.5.5 0 0 1-.5-.5zm-1.496-.854a.5.5 0 0 1 0 .708l-1.5 1.5a.5.5 0 0 1-.708 0l-.5-.5a.5.5 0 0 1 .708-.708l.146.147 1.146-1.147a.5.5 0 0 1 .708 0z"/>
            </svg>
          </router-link>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
    name: 'Sidenav'
}
</script>
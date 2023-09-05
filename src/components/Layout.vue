<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <div>
        <b-navbar class="navbar" type="dark" variant="dark">
            <b-navbar-brand to="/">
                 <img src="../assets/logo5.png" class="d-inline-block align-top" alt="" height="30" width="50">
            </b-navbar-brand>
            <b-navbar-nav>
                <b-nav-item to="/">Home</b-nav-item>
                <b-nav-item to="/movies">Movies</b-nav-item>
                <b-nav-item to="/series">Series</b-nav-item>
            </b-navbar-nav>
        </b-navbar>

        <router-view/>
    </div>
</template>

<style>
  .navbar {
        background-color: #0f0f0f !important;
    }
</style>

<template>
    <header class="header">
        <div class="header-top d-flex justify-content-between py-2 px-4">
            <div class="icons d-flex align-items-center">
                <a href="https://www.facebook.com/profile.php?id=100075583396442" target="_blank">
                    <i class="fab fa-facebook"></i>
                </a>
                <i class="fab fa-instagram" style="display: none;"></i>
            </div>
            <div class="tel-container text-center">
                <i class="fas fa-phone"></i>
                <span>
                    Fale conosco 
                    <a href="https://wa.me/5541984093742" target="_blank" style="white-space: nowrap;">(41) 9 8409-3742</a>
                </span>
            </div>
        </div>
        <div class="header-content row">
            <div class="col-md-9 col-5">
                <nav class="navbar navbar-expand-lg" style="margin-top: 12px;">
                    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#church-navbar" aria-controls="church-navbar" aria-expanded="false" aria-label="Toggle navigation">
                        <i class="fas fa-bars"></i>
                    </button>
                    <div class="collapse navbar-collapse" id="church-navbar">
                        <ul class="navbar-nav ml-auto">
                            <li>
                                <router-link to="/events" class="scroll-top">
                                    EVENTOS
                                </router-link>
                            </li>
                            <li>
                                <router-link to="/give" class="scroll-top">
                                    CONTRIBUA
                                </router-link>
                            </li>
                            <li class="header-icon-container">
                                <router-link to="/" class="scroll-top">
                                    <img src="../assets/img/icon-white.png" class="head-icon" />
                                </router-link>
                            </li>
                            <li>
                                <router-link to="/leadership" class="scroll-top">
                                    PASTORES
                                </router-link>
                            </li>
                            <li>
                                <router-link to="/gallery" class="scroll-top">
                                    GALERIA
                                </router-link>
                            </li>
                        </ul>
                    </div>
                </nav>
            </div>
            <div class="col-md-3 col-7 d-flex align-items-center">
                <button type="button" class="customized-button ml-auto" v-on:click="goToGivePage()">
                    <i class="fas fa-hand-holding-usd"></i>
                    <span style="font-size: calc(.5vw + .5rem);">CONTRIBUA</span>
                </button>
            </div>
        </div>
    </header>
</template>
<script>
export default {
    name: "headerComponent",
    methods: {
        goToGivePage: function () {
            this.$router.push("/give");
        }
    }
}
</script>
<style scoped>

.header {
    position: relative;
    z-index: 10;
}
.head-icon {
    width: calc(1vw + 30px);
}

.header-top {
    font-size: 15px;
    border-bottom: 1px solid white;
}

.header-top i {
    font-size: 20px;
    margin: 0 5px;
    cursor: pointer;
}

.navbar i {
    color: white;
}

.icons i {
    color: white;
}

.tel-container span {
    margin-left: 10px;
}

.tel-container span a {
    margin-left: 5px;
    color: white;
}

.customized-button i {
    margin-right: 10px;
}

.navbar-nav li {
    padding: 10px;
    margin: 5px;
    display: flex;
    align-items: center;
}

.navbar-nav a {
    color: white;
    text-decoration: none;
}

    .navbar-nav a:hover {
        color: rgb(219, 219, 219);
    }

@media (max-width: 991px) {
    .navbar-nav li {
        padding: 10px 10px 10px 0;
        margin: 5px 5px 5px 0;
    }

    .header-icon-container {
        display: none !important;
    }
}
</style>
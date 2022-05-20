<template>
    <ul id="menu">
        <li class="active">Accueil</li>
        <li>A propos</li>
        <li>Projets</li>
        <li>Laboratoire</li>
        <li>Photographie</li>
        <li>Contact</li>
    </ul>
    <i class="fa-solid fa-bars" @click="toggleMenu = !toggleMenu"></i>
        <ul id="mobile_menu" v-if="!toggleMenu" @click="toggleMenu = !toggleMenu">
            <li class="active">Accueil</li>
            <li>A propos</li>
            <li><a href="#">Projets</a></li>
            <li>Laboratoire</li>
            <li>Photographie</li>
            <li>Contact</li>
        </ul>
    
</template>

<script>
export default {
  name: 'Menu',
  data(){
    return {
      toggleMenu: true
    }
  }
}
</script>

<style>
    #menu{
        position: fixed;
        top: 50%;
        left: 100px;
        transform: translateY(-50%);
        list-style: none;
        
    }

    .fa-bars{
        position: fixed;
        right: 19.3%;
        top: 35px;
        font-size: 22px !important;
        color: var(--menu-link-color);
    }

    #menu li{
        color: var(--menu-link-color);
        font-weight: 600;
        opacity: .5;
        cursor: pointer;
    }

    #menu li:hover{
        opacity: 1;
    }

    .active{
        opacity: 1 !important;
    }

    #mobile{
        width: 100%;
        height: 100%;
        position: absolute;
    }

    #menu li::before{
        content: '';
        border-bottom: 2px solid var(--menu-link-color);
        width: 15px;
        position: absolute;
        margin-top: 12px;
        left: 15px;
    }

    #mobile_menu{
        width: 100%;
        position: absolute;
        margin: 0;
        padding: 0;
        background: rgba(255, 255, 255, 0.884);
        height: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
    }

    #mobile_menu li{
        margin: 10px 15px;
        list-style: none;
    }

    @media screen and (max-width:1375px){
        #menu{
            top: 45%;
        }
        #menu li{
            font-size: 14px;
        }
    }

    @media screen and (min-width:1000px){
        #menu{
            display: block;
        }

        .fa-bars{
            display: none;
        }
    }

    @media screen and (max-width:1000px){
        #menu{
            display: none;
        }

        .fa-bars{
            display: block;
        }
    }
</style>
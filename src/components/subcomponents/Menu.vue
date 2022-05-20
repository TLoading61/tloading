<template>
    <ul id="menu">
        <li class="active">Accueil</li>
        <li>A propos</li>
        <li>Projets</li>
        <li>Laboratoire</li>
        <li>Photographie</li>
        <li>Contact</li>
    </ul>
</template>

<script>
export default {
  name: 'Menu'
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

    #menu li::before{
        content: '';
        border-bottom: 2px solid var(--menu-link-color);
        width: 15px;
        position: absolute;
        margin-top: 12px;
        left: 15px;
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
    }

    @media screen and (max-width:1000px){
        #menu{
            display: none;
        }
    }
</style>
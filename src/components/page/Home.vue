<template>
    <div id="home">
        <div id="presentation">
            <h1>Hello World ! Moi, c'est Thomas</h1>
            <h2>Je suis <span class="type"></span></h2>
        </div>
        <div id="acces_projet">
            <a href="#">Voir mes projets</a>
        </div>
    </div>
    
</template>

<script>
import Typed from 'typed.js'

export default {
    name: 'Home',
    mounted(){
        let options = {
            strings: ['développeur web', 'formateur', 'photographe amateur', 'fan de loutres'],
            typeSpeed: 60,
            loop: true,
            backDelay: 1200,
            backSpeed: 20
        }

        new Typed('.type', options)
    }
}
</script>

<style>
    #home{
        height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        max-width: 1180px;
        margin: 0 auto;
    }

    #presentation h1{
        font-size: 70px;
        font-weight: 700;
        color: var(--primary-text-color);
        margin: 0;
        margin-left: 60px;
    }

    #presentation h2{
        font-size: 44px;
        font-weight: 600;
        color: var(--primary-text-color);
        margin: 0;
        margin-left: 60px;
    }

    #presentation span{
        color: var(--secondary-text-color);
    }

    #acces_projet{
        margin-top: 100px;
        text-align: center;
    }

    #acces_projet a{
        color: var(--menu-link-color);
        text-decoration: none;
        border: 1px solid var(--menu-link-color);
        padding: 20px 45px;
    }

    @media screen and (max-width:1600px){
        #presentation h1{
            font-size: 56px;
            margin-left: 150px;
        }

        #presentation h2{
            font-size: 36px;
            margin-left: 150px;
        }
    }

    @media screen and (max-width:1375px){
        #presentation h1{
            font-size: 40px;
            margin-left: 280px;
        }

        #presentation h2{
            font-size: 26px;
            margin-left: 280px;
        }

        #acces_projet a{
            font-size: 14px;
            padding: 20px 25px;
        }
    }

    @media screen and (max-width:1000px){
        #presentation h1{
            font-size: 40px;
            margin-left: 0;
            text-align: center;
        }

        #presentation h2{
            font-size: 26px;
            margin-left: 0;
            text-align: center;
        }
    }
</style>
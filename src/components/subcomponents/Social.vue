<template>
    <div id="social">
        <ul>
            <li><i class="fa-brands fa-instagram"></i></li>
            <li><i class="fa-brands fa-github"></i></li>
            <li><i class="fa-brands fa-linkedin-in"></i></li>
        </ul>
    </div>
</template>

<script>
export default {
  name: 'Social'
}
</script>

<style>
    #social{
        position: fixed;
        bottom: 70px;
        right: 0;
        padding-right: 230px;
        z-index: 10;
    }

    #social ul{
        display: flex;
        list-style: none;
    }

    #social ul::after{
        content: '';
        width: 200px;
        position: absolute;
        right: 0%;
        border-bottom: 1px solid var(--secondary-text-color);
        margin-top: 23px;
    }

    #social ul li{
        font-size: 30px;
        margin: 0 15px;
        color: var(--primary-text-color);
        opacity: .7;
        cursor: pointer;
    }

    #social ul li:hover{
        opacity: 1;
    }

    @media screen and (max-width:600px){
        #social ul::after{
            display: none;
        }

        #social{
            padding: 0;
            width: 100%;
        }

        #social ul{
            padding: 0;
            justify-content: center;
        }
    }
</style>
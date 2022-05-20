<template>
    <div id="nightmode">
        <input type="checkbox" id="checkbox" v-model="darkMode">
        <label for="checkbox" id="label" @click="toggleTheme">
            <i class="fa-solid fa-moon"></i>
            <i class="fa-solid fa-sun"></i>
            <div class="switch"></div>
        </label>
    </div>
</template>

<script>
export default {
  name: 'Night',
  data(){
    return {
      darkMode: false
    }
  },
  watch: {
      darkMode: function () {
          // add/remove class to/from html tag
          let htmlElement = document.documentElement;

          if (this.darkMode) {
              localStorage.setItem("theme", 'dark');
              htmlElement.setAttribute('theme', 'dark');
          } else {
              localStorage.setItem("theme", 'light');
              htmlElement.setAttribute('theme', 'light');
          }
      }
  },
  methods:{
        toggleTheme: function(){
            this.theme = this.theme === "dark-theme" ? "light-theme" : "dark-theme"
        }
  },
  mounted(){
    let bodyElement = document.body;
    bodyElement.classList.add("app-background");
    
    let htmlElement = document.documentElement;
    let theme = localStorage.getItem("theme");

    if (theme === 'dark') {
        htmlElement.setAttribute('theme', 'dark')
        this.darkMode = true
    } else {
        htmlElement.setAttribute('theme', 'light');
        this.darkMode = false
    }
  }
    
}
</script>

<style>
    #nightmode{
        position: absolute;
        left: 19.3%;
        top: 30px;
    }

    #label{
        border: 2px solid var(--secondary-text-color);
        display: flex;
        border-radius: 50px;
        height: 36px;
        width: 75px;
        position: relative;
        align-items: center;
        justify-content: space-around;
        cursor: pointer;
    }

    #checkbox{
        position: absolute;
        opacity: 0;
        z-index: 0;
    }

    .fa-solid{
        font-size: 20px;
    }

    .fa-sun{
        color: #FF9100;
    }
    
    .fa-moon{
        color: #FFFEFE;
    }

    .switch{
        width: 24px;
        height: 24px;
        background: #FF9100;
        position: absolute;
        top: 6px;
        left: 6px;
        border-radius: 50%;
        transition: all .2s linear;
    }

    #checkbox:checked + #label .switch{
        transform: translateX(38px);
        background: #FFFEFE;
    }

    #checkbox:checked + #label{
        border: 2px solid #FFFEFE;
    }

    @media screen and (max-width:1375px){
        #label{
            height: 30px;
            width: 60px;
        }

        .switch{
            width: 20px;
            height: 20px;
            top: 4px;
            left: 4px;
        }

        .fa-solid{
            font-size: 16px;
        }

        #checkbox:checked + #label .switch{
            transform: translateX(30px);
        }
    }
</style>
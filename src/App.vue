<script setup>
import Home from './components/page/Home.vue'
import Menu from './components/subcomponents/Menu.vue'
import Social from './components/subcomponents/Social.vue'
import Night from './components/subcomponents/Night.vue'
import Matter from "matter-js"

</script>

<template>
    <night/>
    <sidenav/>
    <social/>
    <div>
      <div>
        <home/>
      </div>
    </div>
    
</template>

<script>
export default {
  name: 'App',
  components: {
    Home,
    'sidenav' : Menu,
    Social,
    Night
  },
  methods:{
    init: function(){

      const textures = [
        "./src/assets/icons/brain2.svg",
        "./src/assets/icons/code2.svg",
        "./src/assets/icons/hashtag2.svg",
        "./src/assets/icons/laravel2.svg",
        "./src/assets/icons/photo2.svg",
        "./src/assets/icons/github2.svg",
        "./src/assets/icons/terminal2.svg",
        "./src/assets/icons/instagram2.svg",
        "./src/assets/icons/html2.svg",
        "./src/assets/icons/coder2.svg",
        "./src/assets/icons/css2.svg",
        "./src/assets/icons/otter.svg"
      ];

      /*const textures2 = [
        "./src/assets/icons/brain.svg",
        "./src/assets/icons/code.svg",
        "./src/assets/icons/hashtag.svg",
        "./src/assets/icons/laravel.svg",
        "./src/assets/icons/photo.svg",
        "./src/assets/icons/github.svg",
        "./src/assets/icons/terminal.svg",
        "./src/assets/icons/instagram.svg",
        "./src/assets/icons/html.svg",
        "./src/assets/icons/coder.svg",
        "./src/assets/icons/css.svg",
        "./src/assets/icons/otter2.svg"
      ];*/

      const world = document.querySelector("#app");
      const { Engine, Render, Runner, World, Bodies, Body } = Matter;

      let engine = Engine.create();

      let width = window.innerWidth
      let height = window.innerHeight

      let vmin = Math.min(width, height);

      engine.events = {};
      World.clear(engine.world);
      Engine.clear(engine);
      engine = Engine.create();

      let render = Render.create({
        element: world,
        engine: engine,
        options:{
          wireframes: false,
          background: 'transparent',
          width: width,
          height: height
        }
      });

      /*let triangle1 = Bodies.polygon(0, height, 3, 600, {
          isStatic: true,
          render:{
            fillStyle: "transparent"
          }
        });
      Body.rotate(triangle1, 60)
      Body.scale(triangle1, 1, 2)

      let triangle2 = Bodies.polygon(width, height, 3, 600, {
          isStatic: true,
          render:{
            fillStyle: "transparent"
          }
        });
      Body.rotate(triangle2, -82)
      Body.scale(triangle2, 1, 2)*/

      let fond = "";

      if(render.options.width > 700){
          fond = Bodies.rectangle(width / 2, height + 50, width, 100, {
            isStatic: true,
            render: {
                strokeStyle: 'transparent',
            }
        })
      } else {
        fond = Bodies.rectangle(width / 2, height + 50, width, 100, {
            isStatic: false,
            render: {
                strokeStyle: 'transparent',
            }
        })
      }

      World.add(engine.world, [

        fond,
        

        /*triangle1,triangle2,*/
        Bodies.rectangle(-50, height / 2, 100, height, {
            isStatic: true,
            
        }),
        Bodies.rectangle(width + 50, height / 2, 100, height, {
            isStatic: true,
            render: {
                strokeStyle: 'transparent',
                lineWidth: 3
            }
        })


      ]);

      function createBall() {
        const ORIGINAL_SIZE = 240;
        const SIZE = Math.floor(Math.random() * 76) + 30;
        let ball = Bodies.circle(Math.round(Math.random() * width), -30, 29, {
              angle: Math.PI * (Math.random() * 2 - 1),
              friction: 0.001,
              frictionAir: 0.12,
              restitution: 0.8,
              render: {
                  sprite: {
                      texture: textures[

                          Math.floor(Math.random() * (textures.length))],
                      xScale: SIZE / ORIGINAL_SIZE,
                      yScale: SIZE / ORIGINAL_SIZE
                  }
              }
              /*collisionFilter: {
                  category: 0
              }*/
          });

          setTimeout(() => {
              World.remove(engine.world, ball);
          }, 22000);

          return ball;
        }

      Runner.run(engine);

      Render.run(render);
      const handleClick = () => {
          const ball2 = createBall();
          World.add(engine.world, [ball2]);
      };
      setInterval(handleClick, 220)

      
    }
  },
  mounted(){
    this.init();

    //this.init();
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap');

  
  :root{
    --background-color: #FFFEFE;
    --primary-text-color: #81C1AB;
    --secondary-text-color: #EB451E;
    --menu-link-color: #541EEB;
  }

  [theme="dark"] {
    --background-color: #37284a;
    --primary-text-color: #FFFEFE;
    --secondary-text-color: #FFFEFE;
    --menu-link-color: #FFFEFE;
  }

  #app{
    position: relative;
    z-index: 15;
  }

  body{
    margin: 0;
    padding: 0;
    font-family: Poppins;
  }

  .app-background{
    background: var(--background-color);
  }

  canvas{
    position: fixed;
    top: 0;
    pointer-events: none;
  }
</style>
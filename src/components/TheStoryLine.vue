<template>
  <div class="wrapper">
    <nav class="nav__wrapper">
      <ul class="nav">
        <li
          v-for="(link, index) in links"
          :key="index"
          role="presentation"
          :class="{ active: current === link.href.substring(1) }"
        >
          <a :href="link.href">
            <span class="nav__counter">{{ link.counter }}</span>
            <h3 class="nav__title">{{ link.title }}</h3>
            <p class="nav__body">
              <strong>{{ link.body }}</strong>
            </p>
          </a>
        </li>
      </ul>
    </nav>

    <section
      v-for="section in sections"
      :key="section.id"
      ref="section"
      :id="section.id"
      @scroll="handleScroll"
      :class="'section' + ' ' + section.id"
    >
      {{ section.content }}
      <div v-if="section.image && desktopScreen" class="section-image-container">
        <img :src="section.image" class="section-image" />
      </div>
    </section>
  </div>
</template>

<script>
import { ref, onMounted, onBeforeMount } from 'vue'
import { useMatchMedia } from '@/composables/useScreenSize'

export default {
  setup() {
    const desktopScreen = useMatchMedia('(min-width: 1024px)')
    const current = ref('')

    const links = ref([
      {
        href: '#section1',
        counter: '2020',
        title: 'Coding during Lockdown',
        body: "Bored and out of my wits during lockdown, I discovered cheap Udemy courses and started learning in the evenings. After months of late night learning, I completed the Web Developer Bootcamp by Colt Steele, supported by Angela Yu's course when things did not make sense."
      },
      {
        href: '#section2',
        counter: '2021',
        title: 'Apply the knowledge',
        body: 'With just vanilla JavaScript and CSS, I worked on a project to create a digital Rorschach testing tool, while also completing some CSS courses by Travery Media. Later that year, I attended the Bath College Web Development Bootcamp, but before I could finish it, I got hired to work as a fullstack engineer.'
      },
      {
        href: '#section3',
        counter: '2022',
        title: 'Working as a developer',
        body: 'My first job as a developer! What a roller coaster. This is when I realised that there is so much more to know. I learned enough Vue.js and Vuetify to work closely with the UI/UX team on developing a component library, and later on a client facing application with Typescript.'
      },
      {
        href: '#section4',
        counter: '2023',
        title: 'PHP and Laravel',
        body: "A shift in the commpany's priorities meant no more front end team. This is when work with Laravel really took off. We worked on three different applications. The client facing application, the order system application, and the internal billing application."
      },
      {
        href: '#section5',
        counter: '2024',
        title: 'NodeJs and AWS',
        body: 'Yet another shift meant working on developing a document service repository with nodeJs, typescript, terraform and AWS Lambdas, that could listen to events from the client facing application and send them to an S3 bucket and the Inventory service application for validation.'
      },
      {
        href: '#section6',
        counter: 'Now...',
        title: 'Still coding',
        body: 'and still learning to code. When not coding, I like playing the guitar and the piano (badly!), baking, reading, cycling and travelling...'
      }
    ])

    const sections = ref([
      {
        id: 'section1',
        content: ''
      },
      {
        id: 'section2',
        content: ''
      },
      {
        id: 'section3',
        content: ''
      },
      {
        id: 'section4',
        content: ''
      },
      {
        id: 'section5',
        content: ''
      },
      {
        id: 'section6',
        content: ''
      }
    ])

    const handleClick = (event) => {
      const target = document.querySelector(event.target.hash)
      if (target) {
        event.preventDefault()
        window.scrollTo({
          top: target.offsetTop,
          behavior: 'smooth'
        })
      }
    }

    const handleScroll = () => {
      sections.value.forEach((section) => {
        const sectionElement = document.getElementById(section.id)
        const sectionTop = sectionElement?.offsetTop
        const sectionHeight = sectionElement?.clientHeight

        if (window.scrollY >= sectionTop && window.scrollY < sectionTop + sectionHeight) {
          current.value = section.id
        }
      })
    }

    onMounted(() => {
      document.querySelectorAll('a[href*="#"]:not([href="#"])').forEach((link) => {
        link.addEventListener('click', handleClick)
      })
      window.addEventListener('scroll', handleScroll)

      console.log(current.value)
      current.value = 'section1'
    })

    onBeforeMount(() => {
      window.removeEventListener('scroll', handleScroll)
    })

    return {
      handleClick,
      links,
      sections,
      handleScroll,
      current,
      desktopScreen
    }
  }
}
</script>

<style lang="scss" scoped>
.wrapper {
  height: calc(100vh - 200px);
  font-weight: 300;
  color: #fff;
  position: relative;
}

section {
  height: 100vh;
  font-size: 40px;
  font-weight: 100;
  background-color: inherit;

  display: flex;
  justify-content: center;
  align-items: center;

  $colors: white, #f64747, #22a7f0, #f9690e, #9b59b6, #03c9a8c7, #ffcc00c0;
  @for $i from 1 through length($colors) {
    &:nth-child(#{$i}) {
      background: nth($colors, $i);
    }
  }
}

.nav {
  &__wrapper {
    position: fixed;
    display: flex;
    flex-flow: column nowrap;
    justify-content: flex-end;
    left: 50%;
    transform: translateX(-50%);
  }

  & {
    // margin: 0 0 100px 30px;
  }
  &__counter {
    font-size: 24px;
    transition: all 0.15s ease-out;
  }
  &__title {
    font-size: 28px;
    font-weight: 300;
    margin: 0 0 0.25em;
    width: 300px;
    height: 0;
    overflow: hidden;
    opacity: 0;
    transition:
      height 0.3s ease-out,
      opacity 0.2s ease-out;
  }
  &__body {
    font-weight: 100;
    text-align: left;
    margin-top: 10px;
    font-size: 12px;
    width: 300px;
    height: 0;
    overflow: hidden;
    opacity: 0;
    transition:
      height 0.3s ease-out,
      opacity 0.2s ease-out;
  }

  li {
    position: relative;
    transition: all 0.3s ease-out;
    margin-bottom: 1em;

    &:after {
      content: '';
      display: block;
      border-left: 2px solid white;
      border-top: 2px solid white;
      height: 250px;
      width: 20px;
      position: absolute;
      left: -30px;
      top: 15px;
    }

    a {
      display: block;
      padding: 0;
      color: #fff;
      transition: all 0.15s ease-out;

      &:hover {
        background-color: transparent;
        padding-left: 1em;
      }
      &:focus {
        background-color: transparent;
      }
    }

    &.active {
      padding-left: 1em;

      &:after {
        width: 35px;
        height: 400px;
        top: 35px;
      }

      .nav__counter {
        font-size: 40px;
      }
      .nav__title {
        height: 32px;
        opacity: 1;
        overflow: visible;
      }
      .nav__body {
        height: fit-content;
        opacity: 1;
        overflow: visible;
      }
    }
  }
}

@media only screen and (max-width: 767px) {
  .wrapper {
    height: calc(100vh - 200px);
    font-weight: 300;
    position: relative;
  }
  .nav li.active .nav__title {
    max-width: 98%;
    height: fit-content;
  }

  .nav li.active .nav__body {
    max-width: 80%;
  }
}
@media only screen and (min-width: 768px) and (max-width: 1023px) {
  /* Styles for tablet devices */
  .wrapper {
    height: calc(100vh - 200px);
    font-weight: 300;
    position: relative;
    margin: 0 150px;
  }
  .nav li {
    font-size: 22px;
    .nav__counter {
      font-size: 30px;
    }
  }
  .nav li.active {
    .nav__counter {
      font-size: 40px;
    }
    .nav__title {
      max-width: 100%;
    }
    .nav__body {
      max-width: 100%;
      font-size: 16px;
      margin-top: 10%;
    }
  }
}
@media only screen and (min-width: 1024px) {
  /* Styles for desktop devices */
  .wrapper {
    height: calc(100vh - 200px);
    font-weight: 300;
    color: #fff;
    position: relative;
    margin: 0 200px;
  }

  .nav li.active .nav__counter {
    font-size: 50px;
  }

  .nav li.active .nav__body {
    font-size: 16px;
    width: 100%;
  }
  .section-image-container {
    width: 60%;
    height: 60%;
    object-fit: cover;
    margin-right: 20px;
    text-align: center;
    overflow: hidden;
  }

  .section-image {
    max-width: 100%;
    max-height: 100%;
    border-radius: 10%;
  }
  section {
    display: flex;
    flex-direction: row;
    justify-content: flex-end;
    align-items: center;
  }
}
</style>

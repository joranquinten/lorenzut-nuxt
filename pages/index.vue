<template>
  <div>    
    
    <Title :h1="h1" :h2="h2" />

    <section class="mt-20">
        <div class="container text-center">
          <video autoplay loop muted class="mx-auto">
              <source src="/videos/waiting.mp4" type="video/mp4">
              <img src="/img/patandandy.jpg" class="rounded"/>
          </video>
          <p class="text-gray-500 mt-4 mx-auto max-w-xl">This is me pretending to wait for your call. Probably don't hire me for my videography or acting skills.</p>
        </div>
    </section>

    <HomeSection :data="sections('approach')"/>
    <ClickToExpand/>
    <Testimonial :data="$store.state.testimonials[0]"/>
    <HomeSection :data="sections('experience')"/>
    <Testimonial :data="$store.state.testimonials[1]"/>
    <HomeSection :data="sections('contact')"/>
    
  </div>
</template>

<script>
import Title from '~/components/Title.vue'
import HomeSection from '~/components/HomeSection.vue'
import Testimonial from '~/components/Testimonial.vue'
import ClickToExpand from '~/components/ClickToExpand.vue'
export default {
  data(){
    return {
      'h1': "Software Engineer <del>For Hire</del>",
      'h2': "Hey, I'm Patrick, a pragmatic egalitarian - and situational goofball - who likes to leverage his <a href='/#experience' class='link'>diverse tech skills</a> for social good. This is the website I use to land new freelance work. But I'm not taking new clients right now, so... 🤷‍♂️"
    }
  },
  components: {
    Title,
    HomeSection,
    Testimonial,
    ClickToExpand
  },
  methods: {
    sections(slug) {
      return this.$store.state.sections.find(obj => {
        return obj.slug === slug
      })
    },
    externalLinks(){
      for(var c = document.getElementsByTagName("a"), a = 0;a < c.length;a++) {
        var b = c[a];    
        b.getAttribute("href") && b.hostname !== location.hostname && (b.target = "_blank")  
      } 
    }
  },
  head() {
    return {      
      title: 'Patrick Lorenzut: Giggly Software Engineer'
    };
  },
  mounted: function() {
    this.externalLinks()
    window.onclick = function (e) {
      if (e.target.localName == 'a') {
          
      }
    }
  }
}
</script>

<template>
  <main>
    <section class="section flex-center column blue">
      <h1>Basic ScrollTrigger in Nuxt 2</h1>
      <h2>Scroll down to see the magic happen!!</h2>
    </section>
    <div ref="main" class="section flex-center column">
      <div class="box">box</div>
      <div class="box">box</div>
      <div class="box">box</div>
    </div>
    <section class="section flex-center orange column">
      <h1>The End!</h1>
      <h2>
        For more information visit:&nbsp;
        <a
          href="https://greensock.com/scrolltrigger/"
          target="_blank"
          rel="noreferrer"
        >
          greensock.com/scrolltrigger/
        </a>
      </h2>
    </section>
    <header className="header">
      <a
        className="brand"
        href="https://greensock.com/scrolltrigger"
        target="_blank"
        rel="noreferrer"
      >
        <img
          className="greensock-icon"
          src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/scroll-trigger-logo-light.svg"
          width="200"
          height="64"
          alt="ScrollTrigger"
        />
      </a>
    </header>
  </main>
</template>

<script>
import gsap from 'gsap';
import { ScrollTrigger } from 'gsap/ScrollTrigger';

if (typeof window !== 'undefined') {
  gsap.registerPlugin(ScrollTrigger);
}

export default {
  name: 'IndexPage',
  mounted() {
    this.ctx = gsap.context((self) => {
      const boxes = self.selector('.box');
      boxes.forEach((box) => {
        gsap.to(box, {
          x: 150,
          scrollTrigger: {
            trigger: box,
            start: 'bottom bottom',
            end: 'top 20%',
            scrub: true,
          },
        });
      });
    }, this.$refs.main);
  },
  beforeDestroy() {
    this.ctx.revert();
  },
};
</script>

<template>
  <div>
    <ul id="menu">
        <li data-menuanchor="hithere" class="active"><a href="#hithere">Hi there!</a></li>
        <li data-menuanchor="aboutme"><a href="#aboutme">About me</a></li>
        <li data-menuanchor="projects"><a href="#projects">Projects</a></li>
        <li>
            <a href="https://twitter.com/imac2" target="_blank" rel="noopener" class="twitter-share">
                <i>
                    <svg viewBox="0 0 512 512"><path d="M419.6 168.6c-11.7 5.2-24.2 8.7-37.4 10.2 13.4-8.1 23.8-20.8 28.6-36 -12.6 7.5-26.5 12.9-41.3 15.8 -11.9-12.6-28.8-20.6-47.5-20.6 -42 0-72.9 39.2-63.4 79.9 -54.1-2.7-102.1-28.6-134.2-68 -17 29.2-8.8 67.5 20.1 86.9 -10.7-0.3-20.7-3.3-29.5-8.1 -0.7 30.2 20.9 58.4 52.2 64.6 -9.2 2.5-19.2 3.1-29.4 1.1 8.3 25.9 32.3 44.7 60.8 45.2 -27.4 21.4-61.8 31-96.4 27 28.8 18.5 63 29.2 99.8 29.2 120.8 0 189.1-102.1 185-193.6C399.9 193.1 410.9 181.7 419.6 168.6z"></path></svg>
                </i>
            </a>
        </li>
    </ul>
    <ul class="actions">

        <li>
            <a class="actions-button" href="#" rel="noopener" @click="addSection">Add section</a>
        </li>
        <li>
            <a class="actions-button" href="#" rel="noopener" @click="removeSection">Remove section</a>
        </li>
        <li>
            <a class="actions-button" href="#" rel="noopener" @click="toggleNavigation">Toggle nav</a>
        </li>
        <li>
            <a class="actions-button" href="#" rel="noopener" @click="toggleScrollbar">Toggle scrollBar</a>
        </li>
    </ul>
    <full-page :options="options" @after-load="afterLoad" id="fullpage">
      <div class="section" id="section1">
    <div class="bg"></div>
    <div class="column">
      <h3>Hi there!</h3>
      <p>Let´s make the web a better place together</p>
    </div>
  </div>
  <div class="section" id="section2">
    <div class="bg"></div>
    <div class="column">
      <h3>About me</h3>
      <p>I'm Jacinto Melero and I'm a full stack developer
          from <a href="#">Valladolid, Spain</a> <br/>
          I've been working 9 years for a regional administration developing java webapps from scratch. My main goal when I start a project it's to simplify my user's work and ease their transition into a new app.
      </p>
    </div>
  </div>
  <div class="section" id="section3">
    <div class="bg"></div>
    <div class="column">
      <h3>You can take a look
at some of my works: (Click on each one to a brief description)</h3>
    </div>
  </div>
  <div class="section" id="section4">
    <div class="bg"></div>
    <div class="column">
      <h3>You can take a look
at some of my works: (Click on each one to a brief description)</h3>
    </div>
  </div>
    </full-page>
  </div>
</template>

<script>
  import FullPage from 'vue-fullpage.js';
var $ = require("jquery");
  export default {

    components: {
      FullPage,
    },

    data() {
      return {
        options: {
          afterLoad: this.afterLoad,
          scrollBar: false,
          menu: '#menu',
          navigation: true,
          anchors: ['hithere', 'aboutme', 'projects'],
          sectionsColor: ['#fff','#fff','#fff','#b6ea3f','#5ccdc1', '#f89043', '#299a8e', '#ff5f45', '#0798ec', '#fec401', '#1bcee6', '#ee1a59', '#2c3e4f', '#ba5be9', '#b4b8ab'],
          easingcss3: 'cubic-bezier(1.000, -0.440, 0.265, 1.385)',
        },
      }
    },

    methods: {
      afterLoad() {
        console.log("Emitted 'after load' event.");
      },
      addSection: function(e) {
            e.preventDefault();
            var newSectionNumber = $('.fp-section').length + 1;
            console.log(newSectionNumber);
            $('#fullpage').append(`<div class="section">
                <h3>Section ${newSectionNumber}</h3>
            </div>`);

            $('#menu').find('li').last().before(`<li data-menuanchor="page${newSectionNumber}">
                <a href="#page${newSectionNumber}">Section${newSectionNumber}</a>
            </li>`);

            this.options.anchors.push(`page${newSectionNumber}`);

            if(this.options.sectionsColor.length < newSectionNumber){
                this.options.sectionsColor.push(this.options.sectionsColor[newSectionNumber - this.options.sectionsColor.length - 1]);
            }
        },

        removeSection: function(){
            $('#fullpage').find('.fp-section').last().remove();
            this.options.anchors.pop();
            $('#menu').find('li').last().prev().remove();
        },

        toggleNavigation: function(){
            this.options.navigation = !this.options.navigation;
        },

        toggleScrollbar: function(){
            console.log("Changing scrollbar...");
            this.options.scrollBar = !this.options.scrollBar;
        }
    }
  }
</script>
<template>
  <div>
    <ul id="menu">
        <li data-menuanchor="hithere" class="active"><a href="#hithere">Hi there!</a></li>
        <li data-menuanchor="aboutme"><a href="#aboutme">About me</a></li>
        <li data-menuanchor="projects"><a href="#projects">Projects</a></li>
        <li data-menuanchor="projects"><a href="#projects">Skills</a></li>
        <li data-menuanchor="projects"><a href="#projects">Contact</a></li>
    </ul>
    <ul class="actions">
        <li>
            <a class="actions-button" href="#" rel="noopener" @click="addSection">Personal logo</a>
        </li>
        <li>
            <a class="actions-button" href="#" rel="noopener" @click="addSection">LinkedIn</a>
        </li>
        <li>
            <a class="actions-button" href="#" rel="noopener" @click="removeSection">Blog</a>
        </li>
        <li>
            <a class="actions-button" href="#" rel="noopener" @click="toggleNavigation">Mail me</a>
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
          //sectionsColor: ['#fff','#fff','#fff','#b6ea3f','#5ccdc1', '#f89043', '#299a8e', '#ff5f45', '#0798ec', '#fec401', '#1bcee6', '#ee1a59', '#2c3e4f', '#ba5be9', '#b4b8ab'],
          sectionsColor: ['#b6ea3f','#5ccdc1','#f89043','#299a8e','#5ccdc1', '#f89043', '#299a8e', '#ff5f45', '#0798ec', '#fec401', '#1bcee6', '#ee1a59', '#2c3e4f', '#ba5be9', '#b4b8ab'],
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
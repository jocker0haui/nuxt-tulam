<template>
  <header class="header" @click="onScroll" >
    <div class="header__topbar">
      <div class="grid wide">
        <div class="header__topbar__container">
          <div class="row">
            <div class="l-6 m-8 c-8">
              <div class="header__topbar__container--contacts">
                <span>+84 916 425 137</span>
                <a href="#"> <i class="fab fa-pinterest"></i> </a>
                <a href="#"> <i class="fab fa-facebook-f"></i> </a>
                <a href="#"> <i class="fab fa-twitter"></i> </a>
                <a href="#"> <i class="fab fa-dribbble"></i> </a>
                <a href="#"> <i class="fa-brands fa-github"></i> </a>
                <a href="#"> <i class="fa-brands fa-youtube"></i> </a>
              </div>
            </div>
            <div class="l-6 m-4 c-4">
              <div v-if="isLogin" class="header__topbar__container--postAction">
                <a href="#"> avatar </a>
                <span href="">|</span>
                <a href="#"> logout </a>
              </div>
              <div v-else class="header__topbar__container--postAction">
                <a href="#"> login </a>
                <span href="">|</span>
                <a href="#"> register </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="header__nav">
      <div class="header__nav__container">
        <div class="grid wide">
          <div class="row">
            <div class="l-3 m-6 c-8">
              <a href="#">
                <div class="header__nav__container--logo">
                  <img
                    src="https://tranhoangkhang1212.github.io/travelix/assets/images/logo.webp"
                    alt=""
                  />
                  Learn E
                </div>
              </a>
            </div>
            <div class="l-6 hide-on-tablet_mobile">
              <ul class="header__nav__container--list">
                <li><a href="#">Home</a></li>
                <li><a href="#">Courses</a></li>
                <li><a href="#">Blog</a></li>
                <li><a href="#">Contact</a></li>
              </ul>
            </div>
            <div class="l-3 m-6 c-4">
              <i class="fas fa-bars list-tablet-mobile"></i>
              <div class="header__nav__container--search">
                <i id="search" class="fas fa-search" ></i>
                <br />
                <input type="text" placeholder="Search" class="active" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="header__menu">
      <div class="header__menu__overlay"></div>
      <div class="header__menu__body--content">
        <ul>
          <li><a href="#">Home</a></li>
          <li><a href="#">Courses</a></li>
          <li><a href="#">Blog</a></li>
          <li><a href="#">Contact</a></li>
        </ul>
        <i class="fas fa-times"></i>
      </div>
    </div>
    <div class="scroll-top" style="display: none;">
        <i class="fas fa-arrow-up"></i>
    </div>
  </header>
</template>
<script>
export default {
  name: 'CpnHeader',
  data() {
    return {
      isLogin: false,
    }
  },
  
  methods: {
    onScroll() {
      const $ = document.querySelector.bind(document)
      const $$ = document.querySelectorAll.bind(document)
      // Scroll Top
      const scrollTop = () => {
        const header = $('.header')
        header.scrollIntoView({ behavior: 'smooth', block: 'start' })
      }

      const scrollBtn = $('.scroll-top')
      scrollBtn.addEventListener("click", scrollTop);
      window.addEventListener('scroll', scrollBtnDisplay)

      function scrollBtnDisplay() {
        if (
          document.body.scrollTop > 200 ||
          document.documentElement.scrollTop > 200
        ) {
          scrollBtn.style.display = 'block'
        } else {
          scrollBtn.style.display = 'none'
        }
      }

      // Active link header
      const listLink = location.href
      const listItem = $$('.header__nav__container--list a')
      const listLength = listItem.length

      let i = 0
      for (i; i < listLength; i++) {
        if (listItem[i].href === listLink) {
          listItem[i].className = 'active'
        }
      }

      const links = location.href
      const items = $$('.header__menu__body--content a')
      // const listslength = items.length;

      let j = 0
      for (j; j < listLength; j++) {
        if (items[j].href === links) {
          items[j].className = 'active'
        }
      }

      // Header sticky
      const headerSticky = $('.header__nav')
      const topBar = $('.header__topbar')
      window.addEventListener('scroll', scrollFunction)

      function scrollFunction() {
        if (
          document.body.scrollTop > 20 ||
          document.documentElement.scrollTop > 20
        ) {
          headerSticky.classList.add('scroll')
          topBar.classList.add('hide')
        } else {
          headerSticky.classList.remove('scroll')
          topBar.classList.remove('hide')
        }
      }

      // Search Button
      const searchIcon = $('#search')
      if (searchIcon) {
        const input = $('.header__nav__container--search input')
        searchIcon.onclick = function () {
          input.classList.toggle('active')
        }
      }

      // Active link
      const linkList = $$('.header__nav__container--list li')
      const add = function () {
        $('.header__nav__container--list li.active').classList.remove('active')
        this.classList.add('active')
      }
      linkList.forEach((link) => {
        link.addEventListener('click', add)
      })
      // Active Search
      const tabs = $$('.search__container__tab')

      tabs.forEach((tab) => {
        tab.onclick = function () {
          $('.search__container__tab.active').classList.remove('active')
          this.classList.add('active')
        }
      })

      // Header menu modal

      const open = $('#menu_open')
      const close = $('#menu_close')

      if (open) {
        const box = $('.header__menu__overlay')
        const boxBody = $('.header__menu__body--content')
        open.onclick = function () {
          box.style.display = 'block'
          boxBody.classList.add('open')
        }
      }

      if (close) {
        const box = $('.header__menu__overlay')
        const boxBody = $('.header__menu__body--content')
        close.onclick = function () {
          box.style.display = 'none'
          boxBody.classList.remove('open')
        }
      }
    },
  },
}
</script>
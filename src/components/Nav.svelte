<script>
  export let segment, state;
   
  import { goto } from '@sapper/app';

	function toggleAside(event){
    if(window.innerWidth<=750){
      state = !state;
      document.querySelector('.sidenav').classList.toggle('active');
      document.querySelector('body').classList.toggle('noscroll');
      if(state){
        document.querySelector('header img').src = './wcruz.svg';
      } else {
        document.querySelector('header img').src = './logo.svg';
      }	
    }
  }
</script>

<style>
  a, img {
    -webkit-user-select: none;
    -khtml-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    -o-user-select: none;
    user-select: none;
  }
  a img:nth-child(1) {
    margin-right: 10px;
  }
  header:nth-child(2) {
    font-size: 21px;
    margin-top: 2px;
    margin-right: -20px;
  }
  img {
    width: 2em;
  }
  p {
    font-size: 1.5em;
  }
  li a {
    display: flex;
    align-items: center;
    font-size: 18px;
  }
  /* Give every child element its grid name */
  .header {
    grid-area: header;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0 20px;
    background-color: #fff;
  }
  .sidenav {
    grid-area: sidenav;
    display: flex;
    flex-direction: column;
    height: 100%;
    width: 240px;
    position: fixed;
    overflow-y: auto;
    transform: translateX(-245px);
    transition: all .6s ease-in-out;
    box-shadow: 0 2px 2px 0 rgba(0, 0, 0, 0.16), 0 0 0 1px rgba(0, 0, 0, 0.08);
    z-index: 2; /* Needs to sit above the hamburger menu icon */
    background-color: #00171f;
    justify-content: center;
    overscroll-behavior: contain;
    overflow: auto;
    scrollbar-width: none;
  }
  .sidenav::-webkit-scrollbar { /* WebKit */
    width: 0;
    height: 0;
  }
  .sidenav.active {
    transform: translateX(0);
  }
  .sidenav__list {
    padding: 0;
    list-style-type: none;
  }
  .sidenav__list-item {
    display: flex;
    align-items: center;
    padding: 20px 20px 20px 40px;
    white-space: pre;
    color: #eee;
  }
  .sidenav__list-item:hover {
    background-color: rgba(255, 255, 255, 0.2);
    cursor: pointer;
  }
  /* Non-mobile styles, 750px breakpoint */
  @media only screen and (min-width: 46.875em) {
    .sidenav {
      position: relative;
      transform: translateX(0);
    }
  }
</style>
  
<header class="header">
  <p on:click={()=>goto('/')}>Hic et nunc</p>
<!--
  <img src="./logo.svg" alt="Φ" on:click={toggleAside}>
-->
  <p on:click={toggleAside}>Φ</p>
</header>
<aside class="{false ? 'sidenav.active' : 'sidenav'}">
	<ul class="sidenav__list" on:click={toggleAside}>
    <li class="sidenav__list-item">
      <a rel="prefetch" href="about">About</a>
    </li>
    <li class="sidenav__list-item">
      <a rel="prefetch" href="blog">Blog</a>
    </li>
    <li class="sidenav__list-item">
      <a rel="prefetch" href="https://github.com/fchpr/boiler">Source code</a>
    </li>
	</ul>
</aside>
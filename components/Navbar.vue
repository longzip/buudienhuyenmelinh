<template>
  <nav
    class="top-0 absolute z-50 w-full flex flex-wrap items-center justify-between px-2 py-3 "
  >
    <div
      class="container px-4 mx-auto flex flex-wrap items-center justify-between"
    >
      <div
        class="w-full relative flex justify-between lg:w-auto lg:static lg:block lg:justify-start"
      >
        <a
          class="text-sm font-bold leading-relaxed inline-block mr-4 py-2 whitespace-nowrap uppercase text-white"
          href="/"
          >Hồ Thị Thắm - Bưu điện xã Tự Lập</a
        ><button
          class="cursor-pointer text-xl leading-none px-3 py-1 border border-solid border-transparent rounded bg-transparent block lg:hidden outline-none focus:outline-none"
          type="button"
          @click="toggleNavbar()"
        >
          <i class="text-white fas fa-bars"></i>
        </button>
      </div>
      <div
        class="lg:flex flex-grow items-center bg-white lg:bg-transparent lg:shadow-none"
        :class="{'hidden': !showMenu, 'block': showMenu}"
      >
        <ul class="flex flex-col lg:flex-row list-none mr-auto">
          <li class="flex items-center">
            <a
              class="lg:text-white lg:hover:text-gray-300 text-gray-800 px-3 py-4 lg:py-2 flex items-center text-xs uppercase font-bold"
              href="https://shop.thambuudien.ga/"
              target="_blank"
              ><i
                class="lg:text-gray-300 text-gray-500 fa fa-shopping-cart text-lg leading-lg mr-2"
              ></i>
              Cửa hàng</a
            >
          </li>
        </ul>
        <ul class="flex flex-col lg:flex-row list-none lg:ml-auto">
          <li class="flex items-center">
            <a
              class="lg:text-white lg:hover:text-gray-300 text-gray-800 px-3 py-4 lg:py-2 flex items-center text-xs uppercase font-bold"
              href="https://m.me/ThamBuuDien" target="_blank"
              ><i
                class="lg:text-gray-300 text-gray-500 fab fa-facebook-messenger text-lg leading-lg "
              ></i
              ><span class="lg:hidden inline-block ml-2">Facebook</span></a
            >
          </li>
          <li class="flex items-center">
            <a
              class="lg:text-white lg:hover:text-gray-300 text-gray-800 px-3 py-4 lg:py-2 flex items-center text-xs uppercase font-bold"
              href="https://www.instagram.com/thambuudien/"
              ><i
                class="lg:text-gray-300 text-gray-500 fab fa-instagram text-lg leading-lg "
              ></i
              ><span class="lg:hidden inline-block ml-2">Instagram</span></a
            >
          </li>
          <li class="flex items-center">
            <a
              class="lg:text-white lg:hover:text-gray-300 text-gray-800 px-3 py-4 lg:py-2 flex items-center text-xs uppercase font-bold"
              href="https://www.tiktok.com/@hothitham1986"
              ><i
                class="lg:text-gray-300 text-gray-500 fab fa-tiktok text-lg leading-lg "
              ></i
              ><span class="lg:hidden inline-block ml-2">Tiktok</span></a
            >
          </li>
          <li class="flex items-center">
            <a target="_blank" href="https://blog.thambuudien.ga/"
              class="bg-white text-gray-800 active:bg-gray-100 text-xs font-bold uppercase px-4 py-2 rounded shadow hover:shadow-md outline-none focus:outline-none lg:mr-1 lg:mb-0 ml-3 mb-3"
              style="transition: all 0.15s ease 0s;"
            >
              <i class="fa fa-blog"></i> Blog
            </a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>
<script>
export default {
  data() {
    return {
      showMenu: false
    }
  },
  methods: {
    toggleNavbar(){
      this.showMenu = !this.showMenu;
    }
  }
}
</script>

<template>
    <main>


<div id="default-carousel" class="relative" data-carousel="static">
    <!-- Carousel wrapper -->
    <div class="relative h-56 overflow-hidden rounded-lg md:h-96">
         <!-- Item 1 -->
        <div class="hidden duration-700 ease-in-out" data-carousel-item>
            <nuxt-img format="webp" loading="lazy" src="/images/buu-dien-huyen-me-linh-2.png" class="invisible md:visible absolute block w-full -translate-x-1/2 -translate-y-1/2 " alt="Bưu điện huyện mê linh 1" />
            <nuxt-img format="webp" loading="lazy" src="/images/buu-dien-huyen-me-linh.png" class="visible md:invisible absolute block w-full -translate-x-1/2 -translate-y-1/2 " alt="Bưu điện huyện mê linh 2" />
        </div>
        <!-- Item 2 -->
        <div class="hidden duration-700 ease-in-out" data-carousel-item>
            <nuxt-img format="webp" loading="lazy" src="/images/2.jpg" class="absolute block w-full -translate-x-1/2 -translate-y-1/2 " alt="Bưu điện huyện mê linh 3" />
        </div>
        <!-- Item 3 -->
        <div class="hidden duration-700 ease-in-out" data-carousel-item>
            <nuxt-img format="webp" loading="lazy" src="/images/3.jpg" class="absolute block w-full -translate-x-1/2 -translate-y-1/2 " alt="Bưu điện huyện mê linh 4" />
        </div>
    </div>
    <!-- Slider indicators -->
    <div class="absolute z-30 flex space-x-3 -translate-x-1/2 bottom-5 left-1/2">
        <button type="button" class="w-3 h-3 rounded-full" aria-current="false" aria-label="Slide 1" data-carousel-slide-to="0"></button>
        <button type="button" class="w-3 h-3 rounded-full" aria-current="false" aria-label="Slide 2" data-carousel-slide-to="1"></button>
        <button type="button" class="w-3 h-3 rounded-full" aria-current="false" aria-label="Slide 3" data-carousel-slide-to="2"></button>
    </div>
    <!-- Slider controls -->
    <button type="button" class="absolute top-0 left-0 z-30 flex items-center justify-center h-full px-4 cursor-pointer group focus:outline-none" data-carousel-prev>
        <span class="inline-flex items-center justify-center w-8 h-8 rounded-full sm:w-10 sm:h-10 bg-white/30 dark:bg-gray-800/30 group-hover:bg-white/50 dark:group-hover:bg-gray-800/60 group-focus:ring-4 group-focus:ring-white dark:group-focus:ring-gray-800/70 group-focus:outline-none">
            <svg aria-hidden="true" class="w-5 h-5 text-white sm:w-6 sm:h-6 dark:text-gray-800" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path></svg>
            <span class="sr-only">Previous</span>
        </span>
    </button>
    <button type="button" class="absolute top-0 right-0 z-30 flex items-center justify-center h-full px-4 cursor-pointer group focus:outline-none" data-carousel-next>
        <span class="inline-flex items-center justify-center w-8 h-8 rounded-full sm:w-10 sm:h-10 bg-white/30 dark:bg-gray-800/30 group-hover:bg-white/50 dark:group-hover:bg-gray-800/60 group-focus:ring-4 group-focus:ring-white dark:group-focus:ring-gray-800/70 group-focus:outline-none">
            <svg aria-hidden="true" class="w-5 h-5 text-white sm:w-6 sm:h-6 dark:text-gray-800" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path></svg>
            <span class="sr-only">Next</span>
        </span>
    </button>
</div>

      <!-- <Slider /> -->
      <HeroIntro />
      <Team />
      <CTA />
      <!-- <nuxt-img format="webp" loading="lazy" src="/images/buu-dien-huyen-me-linh-2.png"  /> -->
    </main>
</template>
<script>
export default {
  head: {
    title: 'Bưu Điện Huyện Mê Linh - Hà Nội',
    meta: [
      {
        hid: 'description',
        name: 'description',
        content: 'Khu trung tâm hành chính huyện Xã Đại Thịnh, Huyện Mê Linh, Thành phố Hà Nội. Cung cấp dịch vụ bưu chính chuyển phát, đại lý bảo hiểm, ngân hàng và phân phối hàng tiêu dùng.'
      },
      {
            hid: 'og:title',
            property: 'og:title',
            content: 'Bưu Điện Huyện Mê Linh - Hà Nội'
          },
          {
            hid: 'og:description',
            property: 'og:description',
            content: 'Khu trung tâm hành chính huyện Xã Đại Thịnh, Huyện Mê Linh, Thành phố Hà Nội. Cung cấp dịch vụ bưu chính chuyển phát, đại lý bảo hiểm, ngân hàng và phân phối hàng tiêu dùng.'
          },
          {
            hid: 'og:type',
            property: 'og:type',
            content: 'website',
          },
          {
            hid: 'og:image',
            property: 'og:image',
            content: 'https://www.buudienhuyenmelinh.vn/images/buu-dien-huyen-me-linh.png'
          },
          {
            hid: 'og:url',
            property: 'og:url',
            content: 'https://www.buudienhuyenmelinh.vn/'
          },
          {
            property: 'og:locale',
            content: 'vi_VN'
          }
    ],
  }
}
</script>
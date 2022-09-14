<template>
  <div>
    
<nav class="bg-white border-gray-200 dark:bg-gray-900">
    <div class="flex flex-wrap justify-between items-center mx-auto max-w-screen-xl px-4 md:px-6 py-2.5">
        <a href="/" class="flex items-center">
            <img src="/images/logo.png" class="h-24 sm:h-24" alt="Bưu điện huyện Mê Linh Logo">
            <div class="flex flex-col">
<span class="self-left uppercase text-sm font-semibold whitespace-nowrap text-yellow-400 dark:text-white">Tổng công ty</span>
            <span class="self-left uppercase font-semibold whitespace-nowrap text-blue-900 dark:text-white">Bưu điện việt nam</span>
            <span class="self-left tracking-tighter uppercase text-xl font-semibold whitespace-nowrap text-blue-900 dark:text-white">Bưu điện huyện Mê Linh</span>

            </div>
        </a>
        <div class="flex items-center">
            <!-- <a href="tel:0978333963" class="mr-6 text-sm font-medium text-blue-900 dark:text-white hover:underline">0978 333 963</a>
            <a href="#" class="text-sm font-medium text-blue-600 dark:text-blue-500 hover:underline">Đăng nhập</a> -->
        </div>
    </div>
</nav>
<nav class="bg-yellow-400 dark:bg-gray-700">
    <div class="py-3 px-4 mx-auto max-w-screen-xl md:px-6">
        <div class="flex items-center">
            <ul class="flex flex-row mt-0 mr-6 space-x-8 text-sm font-medium">
                <li>
                    <a href="https://shop.buudienhuyenmelinh.vn/" class="text-white dark:text-white hover:underline" aria-current="page">Cửa hàng</a>
                </li>
                <li>
                    <a href="/tra-cuu-hang-buu-dien/" class="text-white dark:text-white hover:underline" aria-current="page">Định vị bưu gửi</a>
                </li>
                <li>
                    <a href="/tra-thoi-han-bao-hiem-y-te/" class="text-white dark:text-white hover:underline">Tra cứu BHYT</a>
                </li>
                <li>
                    <a href="/tinh-muc-dong-va-luong-huu-du-tinh/" class="text-white dark:text-white hover:underline">Tính mức đóng BHXH</a>
                </li>
            </ul>
        </div>
    </div>
</nav>

    <!-- <Navbar /> -->
    <Nuxt />
    <BuuCucs />
    
    <Footer />

    <!-- <Footer /> -->
    <!-- <div class="zalo-chat-widget" data-oaid="907870636305349915" data-welcome-message="Rất vui khi được hỗ trợ bạn!" data-autopopup="0" data-width="" data-height=""></div> -->
        <!-- Messenger Plugin chat Code -->
    <!-- <div id="fb-root"></div> -->

    <!-- Your Plugin chat code -->
    <!-- <div id="fb-customer-chat" class="fb-customerchat">
    </div> -->
    <!-- Google tag (gtag.js) -->
    <script async src="https://www.googletagmanager.com/gtag/js?id=G-QJFM4GBK14"></script>
    <script>
        window.dataLayer = window.dataLayer || [];
        function gtag(){dataLayer.push(arguments);}
        gtag('js', new Date());

        gtag('config', 'G-QJFM4GBK14');
    </script>
    <!-- <script id="mcjs">!function(c,h,i,m,p){m=c.createElement(h),p=c.getElementsByTagName(h)[0],m.async=1,m.src=i,p.parentNode.insertBefore(m,p)}(document,"script","https://chimpstatic.com/mcjs-connected/js/users/03e33e3cdd5e422de02a01d6e/a349bd51a875ff4001de83a79.js");</script> -->
    <!-- <script src="https://sp.zalo.me/plugins/sdk.js"></script> -->
  </div>
</template>
<script>
import "@fortawesome/fontawesome-free/css/all.min.css";
// import 'flowbite';
export default {
  
}
</script>

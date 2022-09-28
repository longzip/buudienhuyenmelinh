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

    <!-- Google tag (gtag.js) -->
    <script async src="https://www.googletagmanager.com/gtag/js?id=G-QJFM4GBK14"></script>
    <script>
        window.dataLayer = window.dataLayer || [];
        function gtag(){dataLayer.push(arguments);}
        gtag('js', new Date());

        gtag('config', 'G-QJFM4GBK14');
    </script>
    <script></script>
  </div>
</template>
<script>
// import 'flowbite';
export default {
  mounted(){
    !function(s,u,b,i,z){var o,t,r,y;s[i]||(s._sbzaccid=z,s[i]=function(){s[i].q.push(arguments)},s[i].q=[],s[i]("setAccount",z),r=["widget.subiz.net","storage.googleapis"+(t=".com"),"app.sbz.workers.dev",i+"a"+(o=function(k,t){var n=t<=6?5:o(k,t-1)+o(k,t-3);return k!==t?n:n.toString(32)})(20,20)+t,i+"b"+o(30,30)+t,i+"c"+o(40,40)+t],(y=function(k){var t,n;s._subiz_init_2094850928430||r[k]&&(t=u.createElement(b),n=u.getElementsByTagName(b)[0],t.async=1,t.src="https://"+r[k]+"/sbz/app.js?accid="+z,n.parentNode.insertBefore(t,n),setTimeout(y,2e3,k+1))})(0))}(window,document,"script","subiz","acrlfufwnwhzkdypguje");
  }
}
</script>

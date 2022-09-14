<template>
    <section class="bg-white dark:bg-gray-900">
    <div class="py-8 px-4 mx-auto max-w-screen-xl text-center lg:py-16 lg:px-6">
        <div class="mx-auto mb-8 max-w-screen-sm lg:mb-16">
            <h2 class="mb-4 text-4xl tracking-tight font-extrabold text-gray-900 dark:text-white">Nhân sự Bưu điện huyện Mê Linh</h2>
            <p class="font-light text-gray-500 sm:text-xl dark:text-gray-400">Thông tin liên hệ của các nhân viên bưu điện Huyện Mê Linh</p>
        </div> 
        <div class="flex overflow-x-auto space-x-16">
            <div v-for="{soDienThoai,hoTen,chucVu,imageUrl} in nhanSus" :key="soDienThoai" class="text-center text-gray-500 dark:text-gray-400">
                <img class="mx-auto mb-4 rounded-full" :src="imageUrl" alt="Bonnie Avatar">
                <h3 class="mb-1 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
                    <a href="#">{{hoTen}}</a>
                </h3>
                <p>{{chucVu}}</p>
                <ul class="flex justify-center mt-4 space-x-4">
                    <li>
                        <a :href="`tel:${soDienThoai}`" class="text-[#39569c] hover:text-gray-900 dark:hover:text-white  inline-flex items-center">
                            <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
    <path d="M2 3a1 1 0 011-1h2.153a1 1 0 01.986.836l.74 4.435a1 1 0 01-.54 1.06l-1.548.773a11.037 11.037 0 006.105 6.105l.774-1.548a1 1 0 011.059-.54l4.435.74a1 1 0 01.836.986V17a1 1 0 01-1 1h-2C7.82 18 2 12.18 2 5V3z"  clip-rule="evenodd" />
  </svg>
                        
                        {{soDienThoai}}</a>
                    </li>
                    
                </ul>
            </div>
            
        </div>  
    </div>
  </section>
</template>

<script>
export default {
    data () {
        return {
            nhanSus: [
                {
                    soDienThoai:'0978333963',
                    hoTen:"Lỗ Văn Tỉnh",
                    chucVu:"Nhân viên kinh doanh",
                    imageUrl: "https://buudienxatulap.ga/images/gui-hang-qua-buu-dien.jpg"
                },  
                {
                    soDienThoai:'0978333963',
                    hoTen:"Lỗ Văn Tỉnh",
                    chucVu:"Nhân viên kinh doanh",
                    imageUrl: "https://buudienxatulap.ga/images/gui-hang-qua-buu-dien.jpg"
                },  
                {
                    soDienThoai:'0978333963',
                    hoTen:"Lỗ Văn Tỉnh",
                    chucVu:"Nhân viên kinh doanh",
                    imageUrl: "https://buudienxatulap.ga/images/gui-hang-qua-buu-dien.jpg"
                },  
                {
                    soDienThoai:'0978333963',
                    hoTen:"Lỗ Văn Tỉnh",
                    chucVu:"Nhân viên kinh doanh",
                    imageUrl: "https://buudienxatulap.ga/images/gui-hang-qua-buu-dien.jpg"
                },  
                {
                    soDienThoai:'0978333963',
                    hoTen:"Lỗ Văn Tỉnh",
                    chucVu:"Nhân viên kinh doanh",
                    imageUrl: "https://buudienxatulap.ga/images/gui-hang-qua-buu-dien.jpg"
                },  
 
                
            ]
        }
    }
}
</script>
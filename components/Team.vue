<template>
    <section class="bg-white dark:bg-gray-900">
    <div class="py-8 px-4 mx-auto max-w-screen-xl text-center lg:py-16 lg:px-6">
        <div class="mx-auto mb-8 max-w-screen-sm lg:mb-16">
            <h2 class="mb-4 text-4xl tracking-tight font-extrabold text-gray-900 dark:text-white">Nhân sự Bưu điện huyện Mê Linh</h2>
            <p class="font-light text-gray-500 sm:text-xl dark:text-gray-400">Thông tin liên hệ của các nhân viên bưu điện Huyện Mê Linh</p>
            <div class="text-center">
                
<div class="inline-flex rounded-md shadow-sm" role="group">
  <button type="button" class="py-2 px-4 text-sm font-medium text-gray-900 bg-white rounded-l-lg border border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-2 focus:ring-blue-700 focus:text-blue-700 dark:bg-gray-700 dark:border-gray-600 dark:text-white dark:hover:text-white dark:hover:bg-gray-600 dark:focus:ring-blue-500 dark:focus:text-white" @click="search = 'Kinh doanh'">
    Kinh doanh
  </button>
  <button type="button" class="py-2 px-4 text-sm font-medium text-gray-900 bg-white border-t border-b border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-2 focus:ring-blue-700 focus:text-blue-700 dark:bg-gray-700 dark:border-gray-600 dark:text-white dark:hover:text-white dark:hover:bg-gray-600 dark:focus:ring-blue-500 dark:focus:text-white"  @click="search = 'BCP hàng'">
    BCP hàng
  </button>
  <button type="button" class="py-2 px-4 text-sm font-medium text-gray-900 bg-white border-t border-b border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-2 focus:ring-blue-700 focus:text-blue-700 dark:bg-gray-700 dark:border-gray-600 dark:text-white dark:hover:text-white dark:hover:bg-gray-600 dark:focus:ring-blue-500 dark:focus:text-white"  @click="search = 'Giao dịch viên'">
    Giao dịch viên
  </button>
  <button type="button" class="py-2 px-4 text-sm font-medium text-gray-900 bg-white rounded-r-md border border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-2 focus:ring-blue-700 focus:text-blue-700 dark:bg-gray-700 dark:border-gray-600 dark:text-white dark:hover:text-white dark:hover:bg-gray-600 dark:focus:ring-blue-500 dark:focus:text-white"  @click="search = 'Bảo hiểm'">
    Bảo hiểm
  </button>
</div>

            </div>
        </div> 
        <div class="flex overflow-x-auto space-x-16">
            <div v-for="{soDienThoai,hoTen,chucVu,imageUrl} in getNhanSus" :key="soDienThoai" class="text-center text-gray-500 dark:text-gray-400">
                <img class="w-24 h-24 mx-auto mb-4 rounded-full" :src="imageUrl" alt="Bonnie Avatar">
                <h3 class="w-44 h-20 mb-1 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
                    <a href="#" class="">{{hoTen}}</a>
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
            search: "",
            nhanSus: [
                {
                    soDienThoai:'0942622200',
                    hoTen:"Lỗ Văn Tỉnh",
                    chucVu:"Kinh doanh",
                    imageUrl: "/images/no-profile-picture-icon.svg"
                },  
                {
                    soDienThoai:'0946548277',
                    hoTen:"Lưu Thị Tuyết Nhung",
                    chucVu:"Kinh doanh",
                    imageUrl: "/images/no-profile-picture-icon.svg"
                },  
                {
                    soDienThoai:'0915.233.199',
                    hoTen:"Nguyễn Thị Thúy Hà",
                    chucVu:"BCP hàng Mê Linh",
                    imageUrl: "/images/no-profile-picture-icon.svg"
                },  
                {
                    soDienThoai:'04.35202106',
                    hoTen:"Phùng Thị Xuân Hương",
                    chucVu:"BCP hàng Thạch Đà",
                    imageUrl: "/images/no-profile-picture-icon.svg"
                },  
                {
                    soDienThoai:'0963720790',
                    hoTen:"Nguyễn Thị Dung",
                    chucVu:"Giao dịch viên",
                    imageUrl: "/images/no-profile-picture-icon.svg"
                },  
                {
                    soDienThoai:'0989805980',
                    hoTen:"Bùi Thị Ngọc Huyền",
                    chucVu:"Giao dịch viên",
                    imageUrl: "/images/no-profile-picture-icon.svg"
                },  
                {
                    soDienThoai:'0396223982',
                    hoTen:"Phạm Thị Hà",
                    chucVu:"Giao dịch viên",
                    imageUrl: "/images/no-profile-picture-icon.svg"
                },  
                {
                    soDienThoai:'097 3847790',
                    hoTen:"Đỗ Thị Thu Thơm",
                    chucVu:"Giao dịch viên",
                    imageUrl: "/images/no-profile-picture-icon.svg"
                },  
                {
                    soDienThoai:'0435202555',
                    hoTen:"Dương Thị Kim Tính",
                    chucVu:"Giao dịch viên",
                    imageUrl: "/images/no-profile-picture-icon.svg"
                },  
                {
                    soDienThoai:'0912.366.657',
                    hoTen:"Trịnh Thị Lan",
                    chucVu:"Bảo hiểm",
                    imageUrl: "/images/no-profile-picture-icon.svg"
                },  
                {
                    soDienThoai:'0367098431',
                    hoTen:"Lỗ Thị Chinh",
                    chucVu:"Bảo hiểm",
                    imageUrl: "/images/no-profile-picture-icon.svg"
                },  
                
 
                
            ]
        }
    },
    computed: {
        getNhanSus() {
            if (!this.search) return this.nhanSus
            return this.nhanSus.filter(n => n.chucVu.includes(this.search))
        }
    }
}
</script>
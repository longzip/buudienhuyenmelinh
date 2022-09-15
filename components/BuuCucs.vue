<template>
    <section class="bg-white dark:bg-gray-900">
  <div class="py-8 px-4 mx-auto max-w-screen-xl lg:py-16 lg:px-6 ">
      <div class="mx-auto max-w-screen-sm text-center mb-8 lg:mb-16">
          <h2 class="mb-4 text-4xl tracking-tight font-extrabold text-gray-900 dark:text-white">Danh sách bưu cục</h2>
          <p class="font-light text-gray-500 lg:mb-16 sm:text-xl dark:text-gray-400">Mạng lưới bưu cục trực thuộc Bưu Điện Huyện Mê Linh.</p>
      </div> 
      <div class="overflow-y-auto h-96 grid gap-8 mb-6 lg:mb-16 md:grid-cols-2">
          <div v-for="{ma,ten,diaChi, website} in buuCucs" :key="ma" class="items-center bg-gray-50 rounded-lg shadow sm:flex dark:bg-gray-800 dark:border-gray-700">
              <div class="p-5">
                  <h3 class="text-xl font-bold tracking-tight text-gray-900 dark:text-white">
                      <a target="_blank" :href="website">{{ten}}</a>
                  </h3>
                  <span class="text-gray-500 dark:text-gray-400">Mã: {{ma}}</span>
                  <p class="mt-3 mb-4 font-light text-gray-500 dark:text-gray-400">Địa chỉ: {{diaChi}}</p>
                  <a target="_blank" :href="`https://www.google.com/maps/search/?api=1&query=${ten}`">Xem đường đi đến bưu cục này</a>
              </div>
          </div> 
      </div>  
  </div>
</section>
</template>
<script>
export default {
    data () {
        return {
            buuCucs: [

                {
                    ma:142240,
                    ten:"TTDV MÊ LINH",
                    diaChi:"Khu trung tâm hành chính huyện, Xã Đại Thịnh, Huyện Mê Linh (ÐT: 02438183999)",
                    website: "/"
                },


                {
                    ma:142000,
                    ten:"Bưu cục Mê Linh",
                    diaChi:"Thôn Đại Bái, Xã Đại Thịnh, Huyện Mê Linh (ÐT: 02438165777)",
                    website: ""
                },

                {
                    ma:142134,
                    ten:"Bưu cục Đại Thịnh",
                    diaChi:"Thôn Đại Bái, Xã Đại Thịnh, Huyện Mê Linh (ÐT: )",
                    website: ""
                },
                {
                    ma:142160,
                    ten:"Bưu cục Tiền Phong",
                    diaChi:"Thôn Yên Nhân, Xã Tiền Phong, Huyện Mê Linh (ÐT: 02432127123)",
                    website: ""
                },


                {
                    ma:142219,
                    ten:"Bưu cục KCN Quang Minh",
                    diaChi:"Sô´Lô 46, Lô 1 đến 46, Khu công nghiệp Quang Minh, Thị Trấn Quang Minh, Huyện Mê Linh (ÐT: 0435202555)",
                    website: ""
                },

         
                
                {
                    ma:142080,
                    ten:"Bưu cục Thạch Đà",
                    diaChi:"Thôn 1, Xã Thạch Đà, Huyện Mê Linh (ÐT: 02438164301)",
                    website: ""
                },
                
                {ma:142180,
                ten:"Điểm BĐVHX Kim Hoa",
                diaChi:"Thôn Phù Trì, Xã Kim Hoa, Huyện Mê Linh (ÐT: 0989588466)",
                website: ""
                },
                {ma:142001,
                ten:"Điểm BĐVHX Tiến Thắng",
                diaChi:"Thôn Bạch Trữ, Xã Tiến Thắng, Huyện Mê Linh (ÐT: 02438154188)",
                website: ""
                },
                {ma:142110,
                ten:"Điểm BĐVHX Thanh Lâm",
                diaChi:"Thôn Đức Hậu, Xã Thanh Lâm, Huyện Mê Linh (ÐT: 02438154192)",
                website: ""
                },
                {ma:142010,
                ten:"Điểm BĐVHX Tự Lập",
                diaChi:"Thôn Phú Mỹ, Xã Tự Lập, Huyện Mê Linh (ÐT: 02438168967)",
                website: ""
                },
                {ma:142030,
                ten:"Điểm BĐVHX Vạn Yên",
                diaChi:"Thôn Yên Nội, Xã Vạn Yên, Huyện Mê Linh (ÐT: 02438164719)",
                website: ""
                },
                {ma:142020,
                ten:"Điểm BĐVHX Liên Mạc",
                diaChi:"Thôn Bồng Mạc, Xã Liên Mạc, Huyện Mê Linh (ÐT: 0912865479)",
                website: ""
                },
                {ma:142070,
                ten:"Điểm BĐVHX Tam Đồng",
                diaChi:"Thôn Tam Báo, Xã Tam Đồng , Huyện Mê Linh (ÐT: 02438164721)",
                website: ""
                },

                {
                    ma:142200,
                    ten:"Điểm BĐVHX Quang Minh",
                    diaChi:"Thôn Gia Thượng, Thị Trấn Quang Minh, Huyện Mê Linh (ÐT: 0975595457)",
                    website: ""
                },
                {ma:142060,
                ten:"Điểm BĐVHX Chu Phan",
                diaChi:"Thôn Chu Phan, Xã Chu Phan, Huyện Mê Linh (ÐT: 0372528135)",
                website: ""
                },
                {ma:142101,
                ten:"Điểm BĐVHX Văn Khê",
                diaChi:"Thôn Văn Quán, Xã Văn Khê, Huyện Mê Linh (ÐT: 02438165675)",
                website: ""
                },
                {ma:142140,
                ten:"Điểm BĐVHX Mê Linh",
                diaChi:"Thôn Hạ Lôi, Xã Mê Linh, Huyện Mê Linh (ÐT: 0353155892)",
                website: ""
                },
                {ma:142090,
                ten:"Điểm BĐVHX Hoàng Kim",
                diaChi:"Thôn Hoàng Xá, Xã Hoàng Kim, Huyện Mê Linh (ÐT: 02438165650)",
                website: ""
                },
                {ma:142040,
                ten:"Điểm BĐVHX Tiến Thịnh",
                diaChi:"Thôn Thọ Lão, Xã Tiến Thịnh, Huyện Mê Linh (ÐT: 0374084699)",
                website: ""
                },
                {ma:142150,
                ten:"Điểm BĐVHX Tráng Việt",
                diaChi:"Thôn Tráng Việt, Xã Tráng Việt , Huyện Mê Linh (ÐT: 0948819996)",
                website: ""
                },
            ]
        }
    }
}
</script>

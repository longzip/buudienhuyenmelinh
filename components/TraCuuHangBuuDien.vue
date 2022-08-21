<template>
    <section class="relative py-20">
        <div class="container mx-auto px-4">
          <div class="items-center flex flex-wrap">
            <div class="w-full md:w-4/12 ml-auto mr-auto px-4">

                <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
                    Mã bưu gửi
                </label>
                <input id="grid-first-name" v-model="searchText" class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" type="text" placeholder="Ví dụ: EB156283795VN" @keydown.enter="timKiem(searchText)">
                <p class="text-red-500 text-xs italic mb-5">Bạn hãy nhập mã vận đơn vào đây và bấm tra cứu.</p>
                <div class="flex items-center justify-between ">
                    <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button" @click="timKiem(searchText)">
                        Tra cứu
                    </button>
                    <a class="inline-block align-baseline font-bold text-sm text-blue-500 hover:text-blue-800" href="tel:0978333963">
                        Bạn cần trợ giúp?
                    </a>
                    </div>
            </div>
            <div class="w-full md:w-4/12 ml-auto mr-auto px-4">
                <div v-if="itemCode && itemCode.TBL_INFO">
                    <p class="text-gray-500 text-xl mt-10">
                        Người gửi: {{itemCode.TBL_INFO.HO_TEN_GUI}}
                    </p>  
                    <p class="text-gray-500 text-xl">
                        Gửi đến: {{itemCode.TBL_INFO.DIA_CHI_NHAN}}
                    </p>
                    <p class="text-gray-500 text-xl">
                        Khối lượng: {{itemCode.TBL_INFO.KHOI_LUONG}}g
                    </p>
                    <h3 class="text-blue-500 text-xl mt-16">Mã vận đơn:{{itemCode.TBL_INFO.MAE1}} - {{itemCode.TBL_INFO.BC_GUI}}</h3>  
                    <ol class="pt-12 relative border-l border-gray-200 dark:border-gray-700">               
                        <li v-for="({NGAY_TRANG_THAI,VI_TRI,TRANG_THAI, DIEN_THOAI},i) in  itemCode.List_TBL_DINH_VI" :key="i" class="mb-10 ml-4">
                            <time class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">{{NGAY_TRANG_THAI}}</time>
                            <h3 class="text-lg font-semibold text-gray-900 dark:text-white">{{VI_TRI}}</h3>
                            <p class="mb-4 text-base font-normal text-gray-500 dark:text-gray-400">{{TRANG_THAI}} {{DIEN_THOAI}}</p>
                            <!-- <a href="tel:0978333963" class="inline-flex items-center py-2 px-4 text-sm font-medium text-gray-900 bg-white rounded-lg border border-gray-200 hover:bg-gray-100 hover:text-blue-700 focus:z-10 focus:ring-4 focus:outline-none focus:ring-gray-200 focus:text-blue-700 dark:bg-gray-800 dark:text-gray-400 dark:border-gray-600 dark:hover:text-white dark:hover:bg-gray-700 dark:focus:ring-gray-700">{{DIEN_THOAI}} <svg class="ml-2 w-3 h-3" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M12.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-2.293-2.293a1 1 0 010-1.414z" clip-rule="evenodd"></path></svg></a> -->
                        </li>
                    </ol>
                    <h3 class="text-lg font-semibold text-blue-900 dark:text-white">Thông tin phát</h3>
                    <ol class="pt-12 relative border-l border-gray-200 dark:border-gray-700">               
                        <li v-for="({NGAY_TRANG_THAI,VI_TRI,TRANG_THAI},i) in  itemCode.List_TBL_DELIVERY" :key="i" class="mb-10 ml-4">
                            <div class="absolute w-3 h-3 bg-gray-200 rounded-full mt-1.5 -left-1.5 border border-white dark:border-gray-900 dark:bg-gray-700"></div>
                            <time class="mb-1 text-sm font-normal leading-none text-gray-400 dark:text-gray-500">{{NGAY_TRANG_THAI}}</time>
                            <h3 class="text-lg font-semibold text-gray-900 dark:text-white">{{VI_TRI}}</h3>
                            <p class="mb-4 text-base font-normal text-gray-500 dark:text-gray-400">{{TRANG_THAI}}</p>
                        </li>
                    </ol>

                    <p class="text-center text-gray-500 text-xs mt-10">
                        &copy;2022 bởi <a href="https://lovanlong.ga">Lỗ Văn Long</a>.
                    </p>
                </div>
                <div v-else>
                    <p class="text-center text-yellow-500 text-2xl pt-16">
                        Hãy nhập mã đơn hàng và bấm tra cứu!
                    </p>
                </div>
                
                </div>
           
          </div>
        </div>
      </section>
</template>
<script>
export default {
    data() {
       return {
           searchText: "",
            itemCode: {},
       } 
    },
    created(){    
        if (this.$route.query.q) {
            const q = this.$route.query.q;
            this.searchText = q;
            this.timKiem(q);
        }
    },
    methods:{
        async fetchAPIByName(searchText){
            const API_URL = `https://api.myems.vn/TrackAndTraceItemCode?itemcode=${searchText}&language=0`;
            const res = await fetch(API_URL, {
                method: 'GET'
            })

            const json = await res.json()
            if (json.errors) {
                throw new Error('Failed to fetch API')
            }
            
            return json;
        },

        async timKiem(searchText){
            this.itemCode = {};
            // this.TBL_INFO = {};

            this.itemCode = await this.fetchAPIByName(searchText);
            // const TBL_INFO = kq;
            // this.TBL_INFO = TBL_INFO;
            // this.itemCode =kq;
        }
    }
}
</script>
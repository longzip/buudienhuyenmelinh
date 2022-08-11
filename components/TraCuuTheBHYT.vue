<template>
    <section class="relative py-20">
        <div class="container mx-auto px-4">
          <div class="items-center flex flex-wrap">
            <div class="w-full md:w-4/12 ml-auto mr-auto px-4">

                <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
                    Mã số BHXH, BHYT:
                </label>
                <input id="grid-first-name" v-model="searchText" class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" type="text" placeholder="Tên" @keydown.enter="timKiem()">
                <p class="text-red-500 text-xs italic mb-5">Nhập mã số thẻ BHYT rồi bấm nút Tra cứu.</p>
                <div class="flex items-center justify-between ">
                    <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button" @click="timKiem()">
                        Tra cứu
                    </button>
                    <a class="inline-block align-baseline font-bold text-sm text-blue-500 hover:text-blue-800" target="_blank" href="https://m.me/103440001315066">
                        Bạn cần trợ giúp?
                    </a>
                    </div>
            </div>
            <div class="w-full md:w-4/12 ml-auto mr-auto px-4">
                <div v-if="dsBhyts.length">
                    <ul v-for="bhyt in dsBhyts" :key="bhyt.maSoBhxh"  class="divide-y divide-gray-200 dark:divide-gray-700 mt-10">
                        <li :class="[bhyt.coTheUuTienCaoHon ? 'bg-yellow-100 border-yellow-500': isConHan(bhyt.denNgayDt) ? 'bg-green-100 border-green-500' : 'bg-gray-100 border-gray-500','py-3 sm:py-4 border-t-4 rounded mb-5 shadow']">
                            <div class="flex-col items-center space-x-4">
                                <div class="min-w-0 mx-5 mb-5">
                                    <p class="text-sm font-medium text-gray-900 dark:text-white text-xl text-bold mb-2">
                                        {{bhyt.hoTen}}
                                        {{bhyt.ngaySinhDt | namSinh}}
                                    </p>
                                    <p class="text-sm text-gray-500 dark:text-gray-400">
                                        Số thẻ BHYT: {{bhyt.soTheBhyt}}
                                    </p>
                                    <p class="text-sm text-gray-500 dark:text-gray-400">
                                        Nơi KCB: {{bhyt.maKCB}}
                                    </p>
                                    <p class="text-sm text-gray-500 dark:text-gray-400">
                                        Từ ngày: {{bhyt.tuNgayDt | ngayThang}}
                                    </p>
                                    <p class="text-sm text-gray-500 dark:text-gray-400 text-xl">
                                        Đến ngày: {{bhyt.denNgayDt | ngayThang}}
                                    </p>
                                    <p class="text-sm text-gray-500 dark:text-gray-400">
                                        Ngày 5 năm liên tục: {{bhyt.ngay5Nam | ngayThangString}}
                                    </p>
                                </div>
                                <div class="flex items-center justify-between text-base font-semibold text-gray-900 dark:text-white">
                                    <div>{{ bhyt.denNgayDt | soNgay}}</div>
                                    <a v-if="!isConHan(bhyt.denNgayDt)" target="_blank" :href="`/gia-han-the-bhyt-tai-nha?maHoGD=${bhyt.maHoGd}&q=${bhyt.maSoBhxh}`" class="mr-5 bg-gray-300 hover:bg-gray-400 text-green-500 font-bold py-2 px-4 rounded inline-flex items-center">Mua ngay</a>
                                </div>
                            </div>
                        </li>
                    </ul>
                    <p class="text-center text-gray-500 text-xs mt-10">
                        &copy;2022 bởi <a href="https://lovanlong.ga">Lỗ Văn Long</a>.
                    </p>
                </div>
                <div v-else>
                    <p class="text-center text-yellow-500 text-xl pt-8">
                        💥 Nếu đã đóng bảo hiểm y tế (BHYT) 5 năm liên tục, bất kì ai cũng có cơ hội được hưởng mức thanh toán 100%. Vậy hiểu như thế nào cho đúng về chế độ BHYT 5 năm liên tục?
                    </p>
                    <p class="text-center text-yellow-500 text-xl pt-8">
                       BHYT 5 năm liên tục là khi người tham gia BHYT có thời gian đóng 05 năm liên tiếp, trong đó được phép gián đoạn tối đa 03 tháng. 
                    </p>
                    <p class="text-center text-yellow-500 text-xl pt-8">
                        🔰 Xem hướng dẫn chi tiết tại: <a target="_blank" href="https://blog.buudienxatulap.ga/posts/bhyt-5-nam-lien-tuc/">https://blog.buudienxatulap.ga/posts/bhyt-5-nam-lien-tuc/</a>
                    </p>
                </div>
                
                </div>
           
          </div>
        </div>
      </section>
</template>
<script>
export default {
    filters: {
        ngayThang (value) {
            if (!value) return ''          
            return new Date(value).toLocaleDateString();
        },
        namSinh (value) {
            if (!value) return ''          
            return new Date(value).toLocaleDateString();
        },
        ngayThangString (value) {
            if (!value) return ''
            if(isNaN(value)) return ''
            return new Date([value.substr(0,4),value.substr(4,2),value.substr(6,2)].join("-")).toLocaleDateString();;
        },
        soNgay(value){
            if (!value) return ''
            const diffTime = (new Date(value) - new Date());
            return (diffTime < 0 ? 'Đã hết ' : 'Còn ') + Math.abs(Math.ceil(diffTime / (1000 * 60 * 60 * 24))) + ' ngày';
        }
    },
    data() {
       return {
           searchText: "",
            dsBhyts: [],
            key: ''
       } 
    },
    created(){
        this.getAuth();      
        if (this.$route.query.q) {
            const q = this.$route.query.q;
            this.searchText = q;
            this.timKiem(q);
        }
    },
    methods:{
        async fetchAPIByName(searchText){
            if(!this.key) await this.getAuth();
            const headers = {
                'Content-Type': 'application/json',
                'Authorization': `Bearer ${this.key}`
            }

            const API_URL = `https://ssm-api.vnpost.vn/api/services/app/TraCuu/TraCuuMaSoBHXH?maTinh=01&maHuyen=250&maXa=08986&hoTen=${searchText}&isCoDau=true&`;

            const res = await fetch(API_URL, {
                method: 'GET',
                headers
            })

            const json = await res.json()
            if (json.errors) {
                throw new Error('Failed to fetch API')
            }
            
            return json.result.value
        },

        async fetchAPIByMaSoBhxh(maSoBhxh){
            if(!this.key) await this.getAuth();
            const headers = {
                'Content-Type': 'application/json',
                'Authorization': `Bearer ${this.key}`
            }

            const API_URL = `https://ssm-api.vnpost.vn/api/services/app/TraCuu/TraCuuThongTinBHYT?maSoBhxh=${maSoBhxh.slice(maSoBhxh.length - 10)}`;

            const res = await fetch(API_URL, {
                method: 'GET',
                headers
            })

            const json = await res.json()
            if (json.errors) {
                throw new Error('Failed to fetch API')
            }
            return json.result
        },

        async fetchUserGhiChu(){
            const headers = {
                'Content-Type': 'application/json'
            }

            const API_URL = 'https://cms.buudienhuyenmelinh.vn/api/user-ghi-chu';

            const res = await fetch(API_URL, {
                method: 'GET',
                headers
            })
            const text = await res.text()
            return text
        },
        
        async save(bhyt){
            const headers = {
                'Content-Type': 'application/json'
            }

            const API_URL = 'https://cms.buudienhuyenmelinh.vn/api/bhyts';

            const res = await fetch(API_URL, {
                method: 'POST',
                headers,
                body: JSON.stringify(bhyt)
            })

            const json = await res.json()
            if (json.errors) {
                // console.error(json.errors)
                throw new Error('Failed to fetch API')
            }
            return json
        },

        async dongBo(maSoBhxh){
            try {
                    const {thongTinTK1, thongTinTheHGD, trangThaiThe} = await this.fetchAPIByMaSoBhxh(maSoBhxh);
                    const theBHYT = {...thongTinTheHGD, ...thongTinTK1, ...trangThaiThe};
                    const found = this.dsBhyts.find(
                        (x) => x.maSoBhxh === theBHYT.maSoBhxh || x.soSoBhxh === theBHYT.soSoBhxh
                    );
                    if(!found) {
                        const bhyt = await this.save(theBHYT)
                        this.dsBhyts.push(bhyt);
                    }
                } catch (error) {
                }
        },

        async timKiem() {
            if(!this.searchText) return;
            const name = this.searchText.split(" ").map(value => value.charAt(0).toUpperCase() + value.slice(1)).join(" ");
            const regex = /[0-9]/g;
            const maSo = this.searchText.match(regex);

            if(maSo){
                await this.dongBo(maSo.join(""));
            }
            else{
                this.dsBhyts = []
                try {
                    const dsBhyts = await this.fetchAPIByName(name);
                    for (let index = 0; index < dsBhyts.length; index++) {
                        const {maSoBhxh} = dsBhyts[index];
                        await this.dongBo(maSoBhxh);
                    }
                } catch (error) {
                    // console.log(error);
                }
            }
        },
        async getTaiTuc(){
            this.dsBhyts = await fetch("https://cms.buudienhuyenmelinh.vn/api/bhyts?thang=2&taiTuc=1&completed=0&disabled=0").then(res =>
                res.json()
            );
        },
        isConHan(value){
            if(!value) return false;
            const diffTime = (new Date(value) - new Date());
            return Math.ceil(diffTime / (1000 * 60 * 60 * 24)) > 90;
        },
        async getAuth(){
            this.key = await this.fetchUserGhiChu();
        }

    }
}
</script>
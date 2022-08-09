<template>
    <section class="relative py-20">
        <div
          class="bottom-auto top-0 left-0 right-0 w-full absolute pointer-events-none overflow-hidden -mt-20"
          style="height: 80px;"
        >
          <svg
            class="absolute bottom-0 overflow-hidden"
            xmlns="http://www.w3.org/2000/svg"
            preserveAspectRatio="none"
            version="1.1"
            viewBox="0 0 2560 100"
            x="0"
            y="0"
          >
            <polygon
              class="text-white fill-current"
              points="2560 0 2560 100 0 100"
            ></polygon>
          </svg>
        </div>
        <div class="container mx-auto px-4">
          <div class="items-center flex flex-wrap">
            <div class="w-full md:w-4/12 ml-auto mr-auto px-4">

                <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
                    Mã số Thẻ BHYT:
                </label>
                <input id="grid-first-name" v-model="searchText" class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" type="text" placeholder="Mã số thẻ BHYT" @keydown.enter="timKiem(searchText)">
                <p class="text-red-500 text-xs italic mb-5">Nhập mã số thẻ BHYT của các thành viên trong hộ gia đình (từng người một) để tra cứu mức đóng.</p>
                <div class="flex items-center justify-between ">
                    <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button" @click="timKiem(searchText)">
                        Tra cứu
                    </button>
                    <a class="inline-block align-baseline font-bold text-sm text-blue-500 hover:text-blue-800" href="tel:0978333963">
                        Bạn cần trợ giúp?
                    </a>
                    </div>
            </div>
            <div class="w-full md:w-8/12 ml-auto mr-auto px-4">
                <div v-if="dsBhyts.length">
                    <div class="flex flex-col">
                        <div class="overflow-x-auto sm:-mx-6 lg:-mx-8">
                            <div class="py-2 inline-block min-w-full sm:px-4 lg:px-4">
                            <div class="overflow-hidden">
                                <h2>Thành viên hộ gia đình:</h2>
                                <table class="min-w-full">
                                <thead class="border-b">
                                    <tr>
                                        <th scope="col" class="text-sm font-medium text-gray-900 px-6 py-4 text-left">
                                            STT
                                        </th>
                                        <th scope="col" class="text-sm font-medium text-gray-900 px-6 py-4 text-left">
                                            Mã thẻ BHYT
                                        </th>
                                        <th scope="col" class="text-sm font-medium text-gray-900 px-6 py-4 text-left">
                                            Họ và tên
                                        </th>
                                        <th scope="col" class="text-sm font-medium text-gray-900 px-6 py-4 text-left">
                                            Ngày sinh
                                        </th>
                                        <th scope="col" class="text-sm font-medium text-gray-900 px-6 py-4 text-left">
                                            Ngày hết hạn
                                        </th>
                                        <th scope="col" class="text-sm font-medium text-gray-900 px-6 py-4 text-left">
                                            Mức đóng
                                        </th>
                                        <th>#</th>
                                    </tr>
                                </thead>
                                <tbody>
                                    <tr v-for="(bhyt, stt) in dsBhyts" :key="bhyt.maSoBhxh" class="border-b">
                                        <td class="px-6 py-4 whitespace-nowrap text-sm font-medium text-gray-900">
                                            {{ stt+1 }}
                                        </td>
                                        <td class="text-sm text-gray-900 font-light px-6 py-4 whitespace-nowrap">
                                            {{ bhyt.soTheBhyt }}
                                        </td>
                                        <td class="text-sm text-gray-900 font-light px-6 py-4 whitespace-nowrap">
                                            {{ bhyt.hoTen }}
                                        </td>
                                        <td class="text-sm text-gray-900 font-light px-6 py-4 whitespace-nowrap">
                                            {{ bhyt.ngaySinhDt | ngayThang }}
                                        </td>
                                        <td class="text-sm text-gray-900 font-light px-6 py-4 whitespace-nowrap">
                                            {{ bhyt | soNgay }}
                                        </td>
                                        <td class="text-sm text-gray-900 font-light px-6 py-4 whitespace-nowrap">
                                            {{ bhyt.tongTien | soTien }} {{ bhyt | daThu}}
                                        </td>
                                        <td>
                                            <button class="text-pink-500 background-transparent font-bold uppercase px-3 py-1 text-xs outline-none focus:outline-none mr-1 mb-1 ease-linear transition-all duration-150" type="button" @click="remove(bhyt.maSoBhxh)">
                                                Hủy
                                            </button>
                                        </td>
                                    </tr>
                                </tbody>
                                </table>
                                <div class="flex  items-center justify-between ">
                                    <div> Tổng cộng: {{ tongCong | soTien }}</div>
                                    <p class="text-xs ">Thông tin chuyển khoản:<br>
                                        Tài khoản: HO THI THAM<br>
                                        Số tài khoản: 0711000234239<br>
                                        Ngân hàng thụ hưởng: Vietcombank<br>
                                        (Hoặc nộp tiền mặt trực tiếp tại Bưu điện xã Tự Lập cạnh trạm y tế xã).
                                    </p>
                                </div>
                            </div>
                            </div>
                        </div>
                    </div>
                        <div class="float-right">
                            <button v-if="tongCong" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button" @click="inKeKhai()">
                                Đồng ý
                            </button>
                        </div>
                    <p class="text-center text-gray-500 text-xs mt-10">
                        &copy;2022 bởi <a href="https://lovanlong.ga">Lỗ Văn Long</a>.
                    </p>
                </div>
                <div v-else>
                    <p class="text-center text-gray-500 text-xs">
                        Không có kết quả phù hợp!
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
            return new Date(value).toISOString().slice(0,4);
        },
        ngayThangString (value) {
            if (!value) return ''
            if(isNaN(value)) return ''
            return new Date([value.substr(0,4),value.substr(4,2),value.substr(6,2)].join("-")).toLocaleDateString();;
        },
        soNgay(value){
            if (!value.denNgayDt) return ''
            if(value.coTheUuTienCaoHon) return 'Có thẻ ưu tiên'
            const diffTime = (new Date(value.denNgayDt) - new Date());
            return (diffTime < 0 ? 'Đã hết ' : 'Còn ') + Math.abs(Math.ceil(diffTime / (1000 * 60 * 60 * 24))) + ' ngày';
        },
        soTien(value){
            if (!value) return ''
            return parseInt(value).toLocaleString();
        },
        daThu(value){
            if(new Date(value.tuNgayDt).toISOString().slice(0,4) === '2022' && value.soTheBhyt.slice(0,2) === 'GD') return "Đã thu"
            return ""
        }
    },
    data() {
       return {
           searchText: "",
            dsBhyts: [],
            mucDong: {
                0: 804600,
                1: 804600,
                2: 563220,
                3: 482760,
                4: 402300 ,
                5: 321840,
            },
            showTaiKhoan: false,
            key: ''    
       } 
    },
    computed:{
        tongCong() {
            return this.dsBhyts.filter(t=>t.tongTien && (t.soTheBhyt.slice(0,2) !== 'GD' || new Date(t.tuNgayDt).toISOString().slice(0,4) !== '2022')).map(t => t.tongTien).reduce((previousValue, currentValue) => previousValue + parseInt(currentValue), 0);
        }
    },
    async created(){
        this.getAuth();
        const {q, maHoGD, maSoBhxhs} = this.$route.query;
        if(maSoBhxhs) {
            await this.getAllByMaSoBhxhs(maSoBhxhs);
            await this.tinhLaiMucDong();
            return;
        }
        if (q) {
            await this.timKiem(q);
        }
        // maHoGd
        if (maHoGD) {
            await this.getAllByMaHoGd(maHoGD);
        }
        this.tinhLaiMucDong();
    },
    methods:{
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
        async getAuth(){
            this.key = await this.fetchUserGhiChu();
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
                        this.capNhatDanhSach([...this.dsBhyts, bhyt]);
                        this.searchText = '';
                    }
                } catch (error) {
                    console.log(error);
                }
        },
        async traCuu(searchText) {
            if(!searchText) return;
            const name = searchText.split(" ").map(value => value.charAt(0).toUpperCase() + value.slice(1)).join(" ");
            const regex = /[0-9]/g;
            const maSo = name.match(regex);
            if(!maSo) return;
            await this.dongBo(maSo);
        },
        async timKiem(searchText) {
            if(!searchText) return;
            const name = searchText.split(" ").map(value => value.charAt(0).toUpperCase() + value.slice(1)).join(" ");
            const regex = /[0-9]/g;
            const maSo = name.match(regex);
            if(!maSo) return;
            const {thongTinTK1, thongTinTheHGD, trangThaiThe} = await this.fetchAPIByMaSoBhxh(maSo.join(""));
            const theBHYT = {...thongTinTheHGD, ...thongTinTK1, ...trangThaiThe};
            // const theBHYTs = await fetch(`https://cms.buudienhuyenmelinh.vn/api/bhyts?&name=${maSo ? maSo.join("") : name}`).then(res =>
            //     res.json()
            // );
            const bhyt = await this.save(theBHYT)
            await this.capNhatDanhSach([bhyt]);
        },
        async getAllByMaHoGd(maHoGd) {
            if(!maHoGd) return;
            const theBHYTs = await fetch(`https://cms.buudienhuyenmelinh.vn/api/bhyts?&maHoGd=${maHoGd}`).then(res =>
                res.json()
            );
            await this.capNhatDanhSach(theBHYTs.filter(item=>item.tuNgayDt));
        },
        async getAllByMaSoBhxhs(maSoBhxhs) {
            if(!maSoBhxhs) return;
            const theBHYTs = await fetch(`https://cms.buudienhuyenmelinh.vn/api/bhyts?&maSoBhxhs=${maSoBhxhs}`).then(res =>
                res.json()
            );
            await this.capNhatDanhSach(theBHYTs.filter(item=>item.tuNgayDt));
        },
        capNhatDanhSach(theBHYTs){
            for (let index = 0; index < theBHYTs.length; index++) {
                const bhyt = theBHYTs[index];
                const diffTime = (new Date(bhyt.denNgayDt) - new Date());
                if(Math.ceil(diffTime / (1000 * 60 * 60 * 24)) < 90){
                    const soNguoiThamGia = this.dsBhyts.filter(item=> (item.tongTien || (new Date(item.tuNgayDt).toISOString().slice(0,4) === '2022' && item.soTheBhyt.slice(0,2) === 'GD'))).length;
                    const thu = soNguoiThamGia < 5 ? soNguoiThamGia + 1 : 5
                    bhyt.tongTien = this.mucDong[thu]
                }
                const found = this.dsBhyts.find(
                    (x) => x.maSoBhxh === bhyt.maSoBhxh
                );
                if (found) Object.assign(found, bhyt);
                else this.dsBhyts.push(bhyt);
            }
            this.taoDonHang();
            
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
        remove(maSoBhxh){
            this.dsBhyts = this.dsBhyts.filter(i => i.maSoBhxh !== maSoBhxh)
            this.tinhLaiMucDong();
        },
        async tinhLaiMucDong(){
            const dsBhytsCopy = [...this.dsBhyts];
            for (let index = 0; index < dsBhytsCopy.length; index++) {
                const bhyt = dsBhytsCopy[index];
                if(bhyt.soTheBhyt.slice(0,2) !== 'GD' || new Date(bhyt.tuNgayDt).toISOString().slice(0,4) !== '2022' )
                    bhyt.tongTien = 0
            }
            this.dsBhyts = [];
            await this.capNhatDanhSach(dsBhytsCopy.filter(item => item.tongTien || (new Date(item.tuNgayDt).toISOString().slice(0,4) === '2022' && item.soTheBhyt.slice(0,2) === 'GD')));
            await this.capNhatDanhSach(dsBhytsCopy.filter(item => !item.tongTien));
        },
        async taoDonHang(){
            const query = Object.assign({}, this.$route.query);
            query.maSoBhxhs= this.dsBhyts.map(item => item.maSoBhxh).join(",");
            await this.$router.push({ query });
        },
        inKeKhai(){
            const a = document.createElement('a');
            a.target = '_blank';
            a.href = `https://cms.buudienhuyenmelinh.vn/thanh-vien-ho-gia-dinh/1/pdf?maSoBhxhs=${this.dsBhyts.map(item => item.maSoBhxh).join(",")}`;
            a.click();
        }
    }
}
</script>
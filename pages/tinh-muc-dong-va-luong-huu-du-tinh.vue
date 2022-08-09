<template>
    <main class="profile-page">
      <section class="relative block pt-16 pb-32 " style="min-height: 75vh;">
        <div
          class="absolute top-0 w-full h-full bg-center bg-cover"
          style='background-image: url("/images/chi-tra-luong-huu.png");'
        >
          <span
            id="blackOverlay"
            class="w-full h-full absolute opacity-75 bg-black"
          ></span>
        </div>
        <div class="container relative mx-auto">
          <div class="items-center flex flex-wrap">
            <div class="w-full lg:w-6/12 px-4 ml-auto mr-auto text-center">
              <div class="pr-12">
                <h1 class="text-white font-semibold text-5xl">
                  Tính mức đóng và lương hưu dự tính.
                </h1>
              </div>
            </div>
          </div>
        </div>
        <div
          class="top-auto bottom-0 left-0 right-0 w-full absolute pointer-events-none overflow-hidden"
          style="height: 70px;"
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
              class="text-gray-300 fill-current"
              points="2560 0 2560 100 0 100"
            ></polygon>
          </svg>
        </div>
      </section>
      <section class="relative py-16 bg-gray-300">
        <div class="container mx-auto px-4">
          <div
            class="relative flex flex-col min-w-0 break-words bg-white w-full mb-6 shadow-xl rounded-lg -mt-64"
          >
            <div class="px-6">
              <section class="pt-20 pb-48">
        <div class="container mx-auto px-4">
          <div class="flex flex-wrap justify-center text-center mb-24">
            <div class="w-full lg:w-6/12 px-4">
              <h2 class="text-4xl font-semibold">Lựa chọn mức đóng và hình thức đóng</h2>
              <p class="text-lg leading-relaxed m-4 text-gray-600">
                Khi tham gia BHXH tự nguyện được NSNN hỗ trợ hộ nghèo bằng 30%, cận nghèo là 25%, đối tượng khác là 10% (tính theo mức chuẩn hộ nghèo nông thôn).
              </p>
              <p class="text-lg leading-relaxed m-4 text-gray-600">
                Từ ngày 01/08/2022 đến hết ngày 31/12/2025, người tham gia BHXH tự nguyện trên địa bàn Hà Nội được hỗ trợ theo tỉ lệ % trên mức đóng hàng hàng: hộ nghèo bằng 30%, cận nghèo là 25%, đối tượng khác là 10% (tính theo mức chuẩn hộ nghèo nông thôn).
              </p>
              <p class="mb-2">
                <select v-model="mucThuNhap">
                  <option disabled value="">Lựa chọn mức thu nhập 👇</option>
                  <option v-for="option in options" :key="option" :value="option">
                    {{ (option*0.22-33000).toLocaleString() }}/{{ option.toLocaleString() }} VNĐ
                  </option>
                </select>
              </p>
              <p><span>Tổng số tiền đóng BHXH 20 năm:</span> {{tongDong20.toLocaleString()}} VNĐ</p>
              <p><strong>Lương hưu dự kiến:</strong> <strong class="text-2xl">{{luongHuu20Nam[0].luong.toLocaleString()}} VNĐ/tháng</strong></p>
              <!-- <p><span>Số tiền gốc:</span> {{tongSoTienGoc.toLocaleString()}} VNĐ</p>
              <p><span>Tổng số tiền cuối kỳ (lãi suất {{Math.round(this.laiSuatNganHang*100)}}%):</span> {{tongSoTienCuoiKy.toLocaleString()}} VNĐ</p>
              <p><span>Số tiền lãi:</span> {{(tongSoTienCuoiKy-tongSoTienGoc).toLocaleString()}} VNĐ</p>
              <p><span>Lãi hàng tháng năm sau 20 năm:</span> {{Math.round(tongSoTienCuoiKy*0.03/12).toLocaleString()}} VNĐ</p> -->
            </div>
          </div>
          <div class="flex flex-wrap">
            <div v-for="item in bangLuaChons" :key="item.soThang" class="w-full md:w-6/12 lg:w-4/12 lg:mb-0 mb-12 px-4">
              <div class="px-4 pb-6">
                <div class="w-72 mx-auto bg-white border-t-4 rounded border-indigo-500 dark:bg-gray-800 shadow text-center p-4">
                    <div class="overflow-hidden">
                        <div class="text-2xl font-medium mb-8 text-gray-800 dark:text-white">
                            Đóng {{item.soThang}} tháng
                        </div>
                        <div class="leading-loose text-sm font-light text-gray-700 dark:text-gray-50 mb-10">
                            <div class="font-bold">
                                Mức thu nhập: {{item.mucThuNhap.toLocaleString()}}
                            </div>
                            <div>
                                Mức đóng theo quy định: {{item.mucDong.toLocaleString()}}
                            </div>
                            <div>
                                NSNN hỗ trợ: {{item.mucHoTro.toLocaleString()}}
                            </div>
                            <div class="text-red-500 text-xl">
                                Hà Nội hỗ trợ: {{item.haNoiHoTro.toLocaleString()}}
                            </div>
                            <div>
                                Lương hưu dự kiến sau 20 năm đóng BHXH
                            </div>
                            <div class="text-gray-500 dark:text-gray-200">
                                <span>
                                    {{item.luongDuKien.nu.toLocaleString()}} VNĐ / Nữ
                                </span>
                            </div>
                            <div class="mb-2 text-gray-500 dark:text-gray-200">
                                <span>
                                    {{item.luongDuKien.nam.toLocaleString()}} VNĐ / Nam
                                </span>
                            </div>
                        </div>
                        <div class="font-bold mb-2 text-gray-500 dark:text-gray-200">
                            <span>
                                {{item.tien.toLocaleString()}} VNĐ
                            </span>
                        </div>
                        
                        <div class="px-4 mt-8 mb-2">
                            <a href="tel:0978333963" class="py-2 px-4  bg-indigo-600 hover:bg-indigo-700 focus:ring-indigo-500 focus:ring-offset-indigo-200 text-white w-full transition ease-in duration-200 text-center text-base font-semibold shadow-md focus:outline-none focus:ring-2 focus:ring-offset-2  rounded-lg ">
                                Bắt đầu
                            </a>
                        </div>
                    </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
      <section class="pt-20 pb-48">
        <div class="container mx-auto px-4">
          <div class="flex flex-wrap justify-center text-center mb-24">
            <div class="w-full lg:w-6/12 px-4">
              <h2 class="text-4xl font-semibold">Hưởng lương hưu sau 20 năm</h2>
              <p class="text-lg leading-relaxed m-4 text-gray-600">
              Bảng dự tính  
              </p>
              <p>
                <select v-model="mucThuNhap">
                  <option disabled value="">Lựa chọn mức thu nhập</option>
                  <option v-for="option in options" :key="option" :value="option">
                    {{ option.toLocaleString() }} VNĐ
                  </option>
                </select> 
                <span>Tỉ lệ hưởng</span>
                <input v-model="tiLeHuong" placeholder="tỉ lệ hưởng" />
              </p>
            </div>
          </div>
          <div class="flex flex-wrap">
            <div v-for="item in luongHuu20Nam" :key="item.namThu" class="w-full md:w-6/12 lg:w-3/12 lg:mb-0 mb-12 px-4">
              <div class="px-6">
                <div :class="[tongDong20<tongNamThu(item.namThu) ? 'border-indigo-500':'border-gray-500', 'w-72 mx-auto bg-white border-t-4 rounded dark:bg-gray-800 shadow text-center p-4']">
                    <div class="overflow-hidden">
                        <div class="text-2xl font-medium mb-8 text-gray-800 dark:text-white">
                            Năm {{item.namThu}}
                        </div>
                        <div class="leading-loose text-sm font-light text-gray-700 dark:text-gray-50 mb-2">
                            <div class="font-bold">
                                Lương tháng: {{item.luong.toLocaleString()}} VNĐ
                            </div>
                            <div>
                                Tổng lương nhận được trong năm
                            </div>
                        </div>
                        <div class="font-bold mb-2 text-gray-500 dark:text-gray-200">
                            <span>
                                {{(item.luong*12).toLocaleString()}} VNĐ
                            </span>
                        </div>
                        <div class="text-gray-500 dark:text-gray-200 text-sm">
                            / năm
                        </div>
                        <div class="px-4 mt-8">
                            <button type="button" class="py-2 px-4  bg-indigo-600 hover:bg-indigo-700 focus:ring-indigo-500 focus:ring-offset-indigo-200 text-white w-full transition ease-in duration-200 text-center text-base font-semibold shadow-md focus:outline-none focus:ring-2 focus:ring-offset-2  rounded-lg ">
                                {{tongNamThu(item.namThu).toLocaleString()}} VNĐ
                            </button>
                        </div>
                    </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
              <HoThiTham />
            </div>
          </div>
        </div>
      </section>
    </main>
</template>

<script>
export default {
  data(){
    return{
      mucThuNhap: 1500000,
      mucHoTro: 33000,
      mucHuong: {
        nam: 0.45,
        nu: 0.55
      },
      tiLeHuong: 0.55,
      tong: 0,
      laiSuatNganHang: 0.07,
      options: [1500000, 2000000, 2500000, 3000000, 3500000, 4000000, 4500000, 5000000, 5500000, 6000000, 6500000, 7000000, 8000000, 9000000, 10000000, 12000000, 15000000, 25000000]
    }
  },
  computed: {
    tongSoTienGoc(){
      return Math.round((this.mucThuNhap*0.22-this.mucHoTro)*12*20)
    },
    tongSoTienCuoiKy(){
      return Math.round((this.mucThuNhap*0.22-this.mucHoTro)*((Math.pow(1+this.laiSuatNganHang/12,12*20+1)-(1+this.laiSuatNganHang/12))/(this.laiSuatNganHang/12)));
    },
    thangHaNoiHoTro(){
      const date = new Date();
      return (2025-date.getFullYear())*12+12-date.getMonth()-1;
    },
    tongDong20(){
      return (this.mucThuNhap*0.22-this.mucHoTro)*120+this.mucThuNhap*0.22*120-this.mucHoTro*(this.thangHaNoiHoTro)
    },
    bangLuaChons(){
      return [1,3,6,12,60].map(soThang => {
        const thangConDuocHaNoiHoTro = soThang < this.thangHaNoiHoTro ? soThang : this.thangHaNoiHoTro
        // console.log(thangConDuocHaNoiHoTro);
        const haNoiHoTro = this.mucHoTro*thangConDuocHaNoiHoTro;
        return {
          soThang,
          mucThuNhap: this.mucThuNhap,
          mucHoTro: this.mucHoTro*soThang,
          haNoiHoTro,
          mucDong: this.mucThuNhap*0.22*soThang,
          luongDuKien: {
            nam: this.mucThuNhap*1.475*this.mucHuong.nam,
            nu: this.mucThuNhap*1.475*this.mucHuong.nu
          },
          tien: ((this.mucThuNhap*0.22-this.mucHoTro)*soThang)-haNoiHoTro
      }});
    },
    luongHuu20Nam(){
      return [...Array(20).keys()].map(namThu => ({
        namThu: namThu + 1,
        luong: Math.round(this.mucThuNhap*1.475*this.tiLeHuong*Math.pow(1.07,namThu))
        }))
    },
  },
  methods: {
    tongNamThu(namThu){
      return [...Array(namThu).keys()].map(i => 
        Math.round(this.mucThuNhap*1.475*this.tiLeHuong*Math.pow(1.07,i)*12)
        ).reduce((partialSum, a) => partialSum + a, 0)
    }
  }
}
</script>

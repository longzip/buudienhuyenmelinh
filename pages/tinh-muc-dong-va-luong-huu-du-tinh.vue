<template>
    <main>
      <section class="bg-white dark:bg-gray-900">
        <div class="py-8 px-4 mx-auto max-w-screen-xl lg:py-16 lg:px-6">
            <div class="mx-auto max-w-screen-md text-center mb-8 lg:mb-12">
                <h1 class="mb-4 text-4xl tracking-tight font-extrabold text-gray-900 dark:text-white">Tính mức đóng và lương hưu dự tính</h1>
                <p class="mb-5 font-light text-gray-500 sm:text-xl dark:text-gray-400">Lựa chọn mức đóng và hình thức đóng</p>
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
            </div>
            <div class="space-y-8 lg:grid lg:grid-cols-4 sm:gap-6 xl:gap-10 lg:space-y-0">
                <!-- Pricing Card -->
                <div v-for="item in bangLuaChons" :key="item.soThang" class="flex flex-col p-6 mx-auto max-w-lg text-center text-gray-900 bg-white rounded-lg border border-gray-100 shadow dark:border-gray-600 xl:p-8 dark:bg-gray-800 dark:text-white">
                    <h3 class="mb-4 text-2xl font-semibold">Đóng {{item.soThang}} tháng</h3>
                    
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
                    <div class="flex justify-center items-baseline my-8">
                        <span class="mr-2 text-3xl font-extrabold">{{item.tien.toLocaleString()}}đ</span>
                        <del class="text-gray-500 dark:text-gray-400">{{(item.tien+item.mucHoTro+item.haNoiHoTro).toLocaleString()}}đ</del>
                    </div>
                    <a  target="_blank" href="https://m.me/103440001315066" class="text-white bg-indigo-600 hover:bg-indigo-700 focus:ring-4 focus:ring-primary-200 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:text-white  dark:focus:ring-primary-900">Bắt đầu</a>
                </div>
            </div>
        </div>
      </section>
      <section class="bg-white dark:bg-gray-900">
        <div class="py-8 px-4 mx-auto max-w-screen-xl lg:py-16 lg:px-6">
            <div class="mx-auto max-w-screen-md text-center mb-8 lg:mb-12">
                <h2 class="mb-4 text-4xl tracking-tight font-extrabold text-gray-900 dark:text-white">Lương hưu dự kiến</h2>
                <p class="mb-5 font-light text-gray-500 sm:text-xl dark:text-gray-400">Tổng lương hưu dự kiến nhận được trong thời gian 20 năm kể từ khi nghỉ hưu</p>
                
            </div>
            <div class="space-y-8 lg:grid lg:grid-cols-4 sm:gap-6 xl:gap-10 lg:space-y-0">
                <!-- Pricing Card -->
                <div v-for="item in luongHuu20Nam" :key="item.namThu" :class="[tongDong20<tongNamThu(item.namThu) ? 'border-indigo-500':'border-gray-100', 'flex flex-col p-6 mx-auto max-w-lg text-center text-gray-900 bg-white rounded-lg border shadow dark:border-gray-600 xl:p-8 dark:bg-gray-800 dark:text-white']">
                    <h3 class="mb-4 text-2xl font-semibold">Năm {{item.namThu}}</h3>
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
      return (2025-date.getFullYear())*12+12-date.getMonth();
    },
    tongDong20(){
      return (this.mucThuNhap*0.22-this.mucHoTro)*120+this.mucThuNhap*0.22*120-this.mucHoTro*(this.thangHaNoiHoTro)
    },
    bangLuaChons(){
      return [1,3,6,12].map(soThang => {
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

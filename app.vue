<template>
  <UApp>
    <div class="flex justify-center items-center" :style="{ backgroundColor: contentBackground }">
      <UCard class="w-full max-w custom-card" :style="{ backgroundColor: contentBackground }">
        <div class="flex justify-center items-center space-x-6 py-4">
          <div class="flex items-center space-x-2">
            <UButton
              class="custom-button-bg header-icon"
              icon="i-heroicons-calendar"
              color="white"
              variant="ghost"
            />
            <p class="text-2xl text-green-500">ปีงบประมาณ 2567</p>
          </div>
          <div class="flex items-center space-x-2">
            <UButton
              class="custom-button-bg header-icon"
              icon="i-mdi-database"
              color="white"
              variant="ghost"
            />
            <p class="text-2xl text-green-500">ด้านการดำรงชีพ</p>
          </div>
          <div class="flex items-center space-x-2">
            <UButton
              class="custom-button-bg header-icon"
              icon="i-heroicons-paper-airplane"
              color="white"
              variant="ghost"
            />
            <p class="text-2xl text-green-500">จังหวัดเลย</p>
          </div>
        </div>
        
        <div class="flex justify-center items-center space-x-4 py-4">
          <div v-for="item in navItems" :key="item.id" class="flex flex-col items-center">
            <UButton
              class="text-xl w-6 h-6 shadow rounded-full flex items-center justify-center custom-button-bg custom-button-icon"
              :icon="item.icon"
              variant="primary"
            />
            <p class="text-sm text-green-500 mt-1">{{ item.title }}</p>
          </div>
        </div>
      </UCard>
    </div>

    
    <div class="p-4" :style="{ backgroundColor: contentBackground }">
     
      <div class="grid grid-cols-3 gap-4">
        
        <UCard class="custom-card">
          <div class="p-4">
            <h2 class="text-lg font-bold text-green-500">
              {{ unitHolding[0].header }}
            </h2>
            <div v-for="item in unitHolding.slice(1)" :key="item.id" class="mt-2 flex justify-between w-full">
              <span class="font-semibold text-left custom-label">
                {{ item.label }}:
              </span>
              <span class="text-right custom-value">{{ item.value }}</span>
            </div>
          </div>
        </UCard>

  
        <UCard class="custom-card">
          <div class="p-4">
            <h2 class="text-lg font-bold text-green-500">
              {{ updateInfo[0].header }}
            </h2>
            <div v-for="item in updateInfo.slice(1)" :key="item.id" class="mt-2 flex justify-between w-full">
              <span class="font-semibold text-left custom-label">
                {{ item.label }}:
              </span>
              <span class="text-right custom-value">
                <template v-if="item.id === 4">
                  <!-- ทำปุ่มกด "ดูประวัติ"-->
                  <UButton
                    variant="outline"
                    class="border border-green-500 text-green-500"
                    size="small"
                    @click="handleHistory"
                  >
                    {{ item.value }}
                  </UButton>
                </template>
                <template v-else>
                  {{ item.value }}
                </template>
              </span>
            </div>
          </div>
        </UCard>

        
        <UCard class="custom-card">
          <div class="p-4">
            <h2 class="text-lg font-bold text-green-500">
              {{ assistanceList[0].header }}
            </h2>
            <div v-for="item in assistanceList.slice(1)" :key="item.id" class="mt-2 flex justify-between w-full">
              <span class="font-semibold text-left custom-label">
                {{ item.label }}:
              </span>
              <span class="text-right custom-value">{{ item.value }}</span>
            </div>
          </div>
        </UCard>
      </div>

      
      <div class="grid grid-cols-3 gap-4 mt-4">
        
        <UCard class="col-span-1 custom-card">
          <div class="p-4">
            <h2 class="text-lg font-bold text-green-500">
              {{ operationPlace[0].header }}
            </h2>
            <div v-for="item in operationPlace.slice(1)" :key="item.id" class="mt-2 flex justify-between w-full">
              <span class="font-semibold text-left custom-label">
                {{ item.label }}:
              </span>
              <span class="text-right custom-value">{{ item.value }}</span>
            </div>
          </div>
        </UCard>

        
        <UCard class="col-span-2 custom-card">
          <div class="p-4">
            
            <div>
              <h2 class="text-lg font-bold text-green-500">
                {{ expense[0].header }}
              </h2>
              <div v-for="item in expense.slice(1)" :key="item.id" class="mt-2 flex justify-between w-full">
                <span class="font-semibold text-left custom-label">
                  {{ item.label }}:
                </span>
                <span class="text-right custom-value">{{ item.value }}</span>
              </div>
            </div>
            
            <div class="mt-4">
              <h2 class="text-lg font-bold text-green-500">
                {{ remainingAmount[0].header }}
              </h2>
              <div v-for="item in remainingAmount.slice(1)" :key="item.id" class="mt-2 flex justify-between w-full">
                <span class="font-semibold text-left custom-label">
                  {{ item.label }}:
                </span>
                <span class="text-right custom-value">{{ item.value }}</span>
              </div>
            </div>
          </div>
        </UCard>
      </div>
    </div>
  </UApp>
</template>

<script setup>
function handleHistory() {
  console.log("History button clicked");
}

const contentBackground = '#F8F8FF';/* พื้นหลังสุด*/

const navItems = [
  { title: "ประกาศเขตการให้ความช่วยเหลือ", icon: "i-mdi-alert-circle", id: 1 },
  { title: "เบิกเงินจากคลัง", icon: "i-mdi-bank", id: 2 },
  { title: "สั่งเอกสารชดใช้เงินทดรองรายการ", icon: "i-mdi-file-document", id: 3 },
  { title: "ตรวจสอบเอกสาร", icon: "i-mdi-check-circle", id: 4 },
  { title: "รมว.มท.เห็นชอบ", icon: "i-mdi-thumb-up", id: 5 },
  { title: "สั่งกรมบัญชีกลาง", icon: "i-mdi-account", id: 6 },
  { title: "หลักการกรมบัญชีกลาง", icon: "i-mdi-lightbulb", id: 7 },
];

const unitHolding = [
  { header: "ข้อมูลหนังสือ", id: 0 },
  { label: "ครั้งที่", value: "1", id: 1 },
  { label: "ลำดับที่", value: "14", id: 2 },
  { label: "เลขที่คำสั่ง", value: "ลย 0021/9708", id: 3 },
  { label: "ชั้นความเร็ว", value: "ด่วนที่สุด", id: 4 },
  { label: "เลขที่สัญญา GFMIS", value: "3600000365", id: 5 },
  { label: "วันที่ออกคำสั่ง", value: "16/03/2567", id: 6 },
  { label: "ประเภท", value: "HR(ปกติ)", id: 7 },
];

const updateInfo = [
  { header: "ข้อมูลภัย",id: 0 },
  { label: "ห้วงเกิดภัย", value: "8/5/2567", id: 1 },
  { label: "วันที่ประกาศภัย", value: "15/7/2567", id: 2 },
  { label: "ขอขยายเวลาถึง", value: "28/7/2567", id: 3 },
  { label: "ประวัติการบันทึกการประชุม", value: "ดูประวัติ", id: 4 },
];

const assistanceList = [
  { header: "รายการช่วยเหลือ",id: 0 },
  { label: "จำนวนเงิน", value: "5.13 ล้านบาท", id: 1 },
  { label: "จำนวนครัวเรือน", value: "320 ครัวเรือน", id: 2 },
];

const operationPlace = [
  { header: "สถานที่ดำเนินการ",id: 0 },
  { label: "อำเภอ", value: "เมืองเลย", id: 1 },
  { label: "เมือง", value: "เมือง", id: 2 },
  { label: "วันครบกำหนดเวลา", value: "45 วัน", id: 3 },
];

const expense = [
  { header: "ค่าใช้จ่าย",id: 0 },
  { label: "จำนวนเงินขออนุมัติ", value: "223,740.00 บาท", id: 1 },
  { label: "จำนวนเงินทั้งหมด(ตามจังหวัด)", value: "554,011.65 บาท", id: 2 },
  { label: "จำนวนเงินทั้งหมด(ตามครั้งที่ขอ)", value: "1,671,623.00 บาท", id: 3 },
];

const remainingAmount = [
  { header: "จำนวนเงินที่เหลือทั้งหมด",id: 0 },
  { label: "ยอดเงินที่เหลือ", value: "11,067,538.20 บาท", id: 1 },
];
</script>

<style lang="scss">
:root {
  --card-background: #ffffff; /* พื้นหลังการ์ด */
  --card-border: #ffffff;  /* สีกรอบการ์ด */
  --label-color: #b7b5b5c7;  /* สีตัวหนังสือข้างหน้า */
  --value-color: #010000c7; /* สีตัวหนังสือข้างหลัง */
  --icon-hover-color: #55cd8f;  /* สีbackground icon ตอนชี้ */
  --icon-default-bg: #ffffff; /* พื้นหลังปุ่มเริ่มต้น */
}

.custom-card {
  background-color: var(--card-background) !important;
  border: 1px solid var(--card-border) !important;
  box-shadow: none !important;
}

.custom-label {
  color: var(--label-color) !important;
}

.custom-value {
  color: var(--value-color) !important;
}


.custom-button-icon {
  background-color: #ffffff !important;
  color: #55cd8f !important; 
  transition: background-color 0.3s ease, color 0.3s ease;
}

.custom-button-icon:hover {
  background-color: var(--icon-hover-color) !important;
  color: #ffffff !important;
}


.header-icon {
  background-color: var(--icon-default-bg) !important;
  color: #55cd8f !important; 
  transition: none !important;
}

.header-icon:hover {
  background-color: var(--icon-default-bg) !important;
  color: #55cd8f !important;
}


.text-green-500 {
  color: #55cd8f !important;
}
</style>



/**
* @Description:    vue-hash-calendar 移动端日期、时间选择插件，日期选择面板以日历形式展示。支持上下滑动切换日期、时间
* @Author:         TSY
* @CreateDate:     2019/05/23 00:08
* @Email:          t@tsy6.com
*/
<template>
  <div class="body">
    <vue-hash-calendar
      pickerType='date'
      :visible="true"
      ref="picker"
      :showTodayButton='false'
      :disabledWeekView='true'
      :markDate='markDate'
      @daka="daka"
      @buqian="buqian"
      :status="status"
                       >
    </vue-hash-calendar>


    <vue-hash-calendar
      pickerType='date'
      :visible="true"
      ref="picker1"
      :showTodayButton='false'
      :disabledWeekView='true'
      :markDate='markDate1'
      @daka="daka1"
      @buqian="buqian"
      :status="status2"
                       >
    </vue-hash-calendar>
  </div>
</template>

<script>
import Github from './Github.vue'

export default {
  name: 'demo',
  components: { Github },
  data() {
    return {
      status: 1,
      markDate: [
        '2020/3/24', '2020/3/22'
      ],
      status2: 2,
      markDate1: [
        '2020/3/24', '2020/3/22'
      ]
    }
  },
  mounted() {
    //            this.defaultDatetime = new Date('2018-01-01 12:04');
  },
  methods: {
    showCalendarDialog() { // 显示日历
      this.isShowCalendar = true
    },
    dateChange(date) { // 日期改变触发
      console.log(date, 'change')
    },
    dateConfirm(date) { // 点击确认按钮触发
      console.log(date, 'confirm')
    },
    dateClick(date) { // 点击日期时按钮触发
      console.log(date, 'click')
    },
    disabledDate(date) { // 禁用的日期
      let timestamp = date.getTime()
      let oneDay = 24 * 60 * 60 * 1000

      if (timestamp < new Date().getTime() - oneDay) {
        return true
      }

      return false
    },
    daka() {
      this.isSign = true
      this.markDate = ['2020/3/24', '2020/3/22', '2020/3/28']
      console.log('daka')
    },
    daka1() {
      this.isSign1 = true
      this.markDate1 = ['2020/3/24', '2020/3/22', '2020/3/28']
      console.log('daka')
    },
    buqian() {
      console.log('buqian')
    }
  }
}
</script>

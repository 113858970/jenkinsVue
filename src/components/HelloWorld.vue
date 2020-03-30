<template>
  <div>
    <input v-model="msg">
    <p>msg: {{ msg }}</p>
    <p @click="modalShow">弹出框</p>
    <div v-if="isShow">
      <confirm-modal
        :type="confirmModal.type"
        :title="confirmModal.title"
        :content="confirmModal.content"
        :cancelText="confirmModal.cancelText"
        :submitText="confirmModal.submitText"
        :cssStyle="confirmModal.cssStyle"
        :noneToastText="confirmModal.noneToastText"
        :isMarginTop="confirmModal.isMarginTop"
        @onHandleCancel="handleOnCancel"
        @onHandleOnOk="handleOnOk"
      />
    </div>
  </div>
</template>

<script>
import ConfirmModal from 'ad-dialog'
//  @Component
export default {
  data () {
    return {
      isShow: false,
      confirmModal: {
        // type: 'input',
        title: '请输入用户名',
        content: '你要给我点个赞嘛 ?',
        cancelText: '取消',
        submitText: '确认',
        cssStyle: {
          bgTitleColor: '#4d4d4d',
          textTitleColor: '#ffffff',
          bgCancelColor: '#fff',
          textCancelColor: '#555',
          bgSubmitColor: '#4d4d4d',
          textSubmitColor: '#fff'
        },
        isMarginTop: '35%'
      },
      msg: 1133
    }
  },
  // 声明周期钩子
  mounted () {
    // this.greet()
  },
  methods: {
    modalShow () {
      this.isShow = true
    },
    // submit
    handleOnOk (type, bool, value) {
      if (type === 'normal') {
        console.log(type, bool, value) // normal  true  ''
      } else {
        console.log(type, bool, value) // normal  true  value
      }
      this.isShow = false
    },
    // cancel
    handleOnCancel (type, bool) {
      console.log('console', type, bool)
      this.isShow = false
    }
  },
  components: {
    ConfirmModal
  }
}
</script>

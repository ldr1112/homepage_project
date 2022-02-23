<template>
  <div>
    <b-navbar toggleable="lg" type="dark" variant="dark">
      <!-- assets에 있는 이미지 파일은 경로를 @/assets/2.png 이렇게 해야함 -->
      <img src='@/assets/골대1.png' style = "margin-left: 15px">
      <b-navbar-brand href="#" to="/" style = "margin-left: 15px">농구데스매치</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav>
          <b-nav-item to="/TeamJoin/free">팀 등록</b-nav-item>
          <b-nav-item-dropdown text="매치 게임" right>
            <b-dropdown-item href="#">3대3 매치</b-dropdown-item>
            <b-dropdown-item href="#">5대5 매치</b-dropdown-item>
          </b-nav-item-dropdown>
          <b-nav-item href="#">토너먼트 게임</b-nav-item>
          <b-nav-item to="/board/free">자유게시판</b-nav-item>

          <b-nav-item style="float:right">
            <b-button  v-b-modal.modal-prevent-closing>로그인</b-button>
            <b-modal
              id="modal-prevent-closing"
              ref="modal"
              title="로그인을 해주세요"
              @show="resetModal"
              @hidden="resetModal"
              @ok="handleOk"
            >
              <form ref="form" @submit.stop.prevent="handleSubmit">
                <b-form-group
                  label="아이디"
                  label-for="name-input"
                  invalid-feedback="Name is required"
                  :state="nameState"
                >
                <b-form-input
                  id="name-input"
                  v-model="name"
                  :state="nameState"
                  required
                ></b-form-input>
                </b-form-group>
              </form>
            </b-modal>
          </b-nav-item>  
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
    
  </div>
</template>
<script>
export default {
  name: "Header",
  data() {
    return {
      name: '',
      nameState: null,
      submittedNames: []
    }
  },
   methods: {
      checkFormValidity() {
        const valid = this.$refs.form.checkValidity()
        this.nameState = valid
        return valid
      },
      resetModal() {
        this.name = ''
        this.nameState = null
      },
      handleOk(bvModalEvt) {
        // Prevent modal from closing
        bvModalEvt.preventDefault()
        // Trigger submit handler
        this.handleSubmit()
      },
      handleSubmit() {
        // Exit when the form isn't valid
        if (!this.checkFormValidity()) {
          return
      }
        // Push the name to submitted names
        this.submittedNames.push(this.name)
        // Hide the modal manually
        this.$nextTick(() => {
        this.$bvModal.hide('modal-prevent-closing')
      })
    }
  }
}
</script>
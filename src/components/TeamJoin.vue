<template>
  <div>
    <!-- 팀 이름 -->
    <b-container fluid>
      <b-row class="my-1" v-for="type in types" :key="type">
        <b-col sm="3">
          <label :for="`type-${type}`">팀 이름: </label>
        </b-col>
        <b-col sm="3">
          <b-form-input :id="`type-${type}`" :type="type"></b-form-input>
        </b-col>
      </b-row>
    </b-container>

    <!-- 팀 소개 -->
    <b-container fluid>
      <b-row>
        <b-col sm="2">
          <label for="textarea-small">팀 소개</label>
        </b-col>
        <b-col sm="10">
          <b-form-textarea
            id="textarea-small"
            size="sm"
            placeholder="팀 소개글을 적어주세요"
          ></b-form-textarea>
        </b-col>
      </b-row>
    </b-container>
    
    <!-- 지역 -->
    <label for="rating-sm">지역</label>
    <b-form-select v-model="selected" :options="options"></b-form-select>

    <!-- 경기 방식 -->
    <b-form-group label="경기 방식" v-slot="{ ariaDescribedby }">
      <b-form-radio-group
        id="radio-group-1"
        v-model="selected"
        :aria-describedby="ariaDescribedby"
        name="radio-sub-component1"
      >
      <b-form-radio value="first">3대3 경기</b-form-radio>
      <b-form-radio value="second">5대5 경기</b-form-radio>
      <b-form-radio value="third">둘다 가능</b-form-radio>
      </b-form-radio-group>
    </b-form-group>

    <!-- 실력 -->
    <b-form-group label="실력" v-slot="{ ariaDescribedby }">
      <b-form-radio-group
        id="radio-group-2"
        v-model="selected"
        :aria-describedby="ariaDescribedby"
        name="radio-sub-component2"
      >
        <b-form-radio value="first">상</b-form-radio>
        <b-form-radio value="second">중</b-form-radio>
        <b-form-radio value="third">하</b-form-radio>
        <b-form-radio value="fourth">최하</b-form-radio>
      </b-form-radio-group>
    </b-form-group>

    <!-- 매너 -->
    <label for="rating-sm">매너</label>
    <b-form-rating v-model="value" variant="warning" class="mb-2"></b-form-rating>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        types: [
          'text',
        ],
        selected: null,
        options: [
          { value: null, text: '지역을 골라주세요' },
          { value: '1', text: '서울' },
          { value: '2', text: '부산' },
          { value: '3', text: '대구' },
          { value: '4', text: '인천' },
          { value: '5', text: '광주' },
          { value: '6', text: '대전' },
          { value: '7', text: '울산' },
          { value: '8', text: '세종' },
          { value: '9', text: '경기도' },
          { value: '10', text: '강원도' },
          { value: '11', text: '충청북도' },
          { value: '12', text: '충청남도' },
          { value: '13', text: '전라북도' },
          { value: '14', text: '전라남도' },
          { value: '15', text: '경상북도' },
          { value: '16', text: '경상남도' },
          { value: '17', text: '제주도' },
        ]
      }
    }
  }
</script>
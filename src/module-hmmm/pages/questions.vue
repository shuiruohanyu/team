<template>
  <div class="question-container">{{provinces}}{{citys}}</div>
</template>

<script>
import {
  list as questionList,
  remove as questionRemove
} from "../../api/hmmm/questions";
import { list as subjectList } from "../../api/hmmm/subjects";
import { questionType, difficulty } from "../../api/hmmm/constants";
import { provinces, citys } from "../../api/hmmm/citys";
export default {
  data() {
    return {
      list: [],
      subjects: [],
      questionType,
      difficulty,
      provinces: provinces(),
      citys: citys("北京市")
    };
  },
  methods: {
    async getQuestion() {
      let result = await questionList();
      this.list = result.data;
    },
    async getSubject() {
      let result = await subjectList();
      this.subjects = result.data;
    }
  },
  created() {
    this.getQuestion();
    this.getSubject();
  }
};
</script>

<style lang="scss"></style>

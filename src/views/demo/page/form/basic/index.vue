<template>
  <PageWrapper
    title="基础表单"
    contentBackground
    content=" 表单页用于向用户收集或验证信息，基础表单常见于数据项较少的表单场景。"
    contentClass="p-4"
  >
    <BasicForm @register="register" />
    <span>{{ service.name }}</span>
    <a-button @click="setField">hello</a-button>
  </PageWrapper>
</template>
<script lang="ts" setup>
  import { BasicForm } from '/@/components/Form';
  import { ref, onMounted } from 'vue';
  import { Service } from './data';
  // import { useMessage } from '/@/hooks/web/useMessage';
  import { PageWrapper } from '/@/components/Page';

  const service = ref(new Service());
  const [register, { getFormModel }] = service.value.initForm();
  onMounted(async () => {
    service.value.formModel = await getFormModel();
    service.value.name = '123';
    console.log(service.value.name);
  });
  function setField() {
    service.value.name = '456';
  }
</script>
<style lang="less" scoped>
  .form-wrap {
    padding: 24px;
    background-color: @component-background;
  }
</style>

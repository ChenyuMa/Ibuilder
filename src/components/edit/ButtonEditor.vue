<template>
  <div>
    <div class="subEditor">
      <form-item-title :title="'文字'"></form-item-title>
      <div class="field-wrap">
        <div class="field is-horizontal">
          <div class="field-label is-small">
            <label class="label">文本</label>
          </div>
          <div class="field-body">
            <div class="field">
              <div class="control">
                <input class="input is-small" type="text" v-model="$store.state.editorData.text">
              </div>
            </div>
          </div>
        </div>
        <div class="field is-horizontal">
          <div class="field-label is-small">
            <label class="label">字体</label>
          </div>
          <div class="field-body">
            <div class="field">
              <div class="control">
                <input class="input is-small" type="text" v-model="$store.state.editorData.s['font-family']">
              </div>
            </div>
          </div>
        </div>
        <div class="field is-horizontal">
          <div class="field-label is-small">
            <label class="label">字号</label>
          </div>
          <div class="field-body">
            <div class="field">
              <div class="control">
                <input class="input is-small" type="text" v-model="$store.state.editorData.s['font-size']">
              </div>
            </div>
          </div>
        </div>
        <div class="field is-horizontal">
          <div class="field-label is-small">
            <label class="label">字体粗细</label>
          </div>
          <div class="field-body">
            <div class="field">
              <div class="control">
                <input class="input is-small" type="text" v-model="$store.state.editorData.s['font-weight']">
              </div>
            </div>
          </div>
        </div>
        <div class="field is-horizontal">
          <div class="field-label is-small">
            <label class="label">字体颜色</label>
          </div>
          <div class="field-body">
            <div class="field">
              <div class="control">
                <input class="input is-small" type="color" v-model="$store.state.editorData.s['color']">
              </div>
            </div>
          </div>
        </div>
      </div>

      <form-item-title :title="'事件'"></form-item-title>
      <div class="field-wrap">
        <div class="field is-horizontal">
          <div class="field-label is-small">
            <label class="label">跳转</label>
          </div>
          <div class="field-body">
            <div class="field">
              <div class="control">
                <div class="select is-small">
                  <select v-model="$store.state.editorData.goto">
                    <option v-for="(item, index) in $store.state.allPageList" :key="index" :value="item.id">
                      {{item.title}}
                    </option>
                  </select>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="field is-horizontal">
          <div class="field-label is-small">
            <label class="label">弹窗</label>
          </div>
          <div class="field-body">
            <div class="field">
              <div class="control">
                <input class="input is-small" type="text" v-model="$store.state.editorData.modal">
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <attr-editor></attr-editor>
  </div>
</template>

<script>
  import AttrEditor from "@/components/AttrEditor.vue"
  import FileUpLoad from "@/components/FileUpLoad.vue"
  import formItemTitle from '../formItemTitle'
  export default {
    components: {
      AttrEditor,
      FileUpLoad,
      formItemTitle
    }
  }

</script>

<style lang="less" scoped>
  .subEditor {
    margin-top: 0.75rem;
  }

</style>

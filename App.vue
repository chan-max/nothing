<template>
  <div style="width: 80vw; margin-top: 10vh; margin-left: 10vw">
    <div style="width: 100%; height: 100%">
      <template v-if="isFirstSubmit">
        <div style="width: 480px">
          <div style="display: flex">
            <div class="form-title">标题</div>
            <div class="form-title">选择</div>
          </div>
          <div style="display: flex; flex-direction: column; padding: 64px 36px">
            <div
              style="display:flex;items-center;padding:8px;justify-content: space-between;"
              class="form-item"
              v-for="item in list"
            >
              <div class="form-label">{{ item.CHANNEL_NM }}</div>

              <div>
                <el-radio-group
                  v-model="item.radioValue"
                  :disabled="item.EDIT_STATUS == '1'"
                >
                  <el-radio label="0">ON</el-radio>
                  <el-radio label="1">OFF</el-radio>
                </el-radio-group>
              </div>
            </div>
          </div>
        </div>
      </template>

      <template v-else>
        <div style="display: flex; column-gap: 24px">
          <div style="width: 480px">
            <div style="display: flex">
              <div class="form-title">标题</div>
              <div class="form-title">修改前</div>
            </div>

            <div style="display: flex; flex-direction: column; padding: 64px 36px">
              <div
                class="form-item"
                style="display:flex;items-center;padding:8px;justify-content: space-between;"
                v-for="item in list"
              >
                <div class="form-label">{{ item.CHANNEL_NM }}</div>

                <div>
                  {{ item.CHANNEL_AUTH_FLG == "0" ? "ON" : "OFF" }}
                </div>
              </div>
            </div>
          </div>

          <div style="width: 480px">
            <div style="display: flex">
              <div class="form-title">标题</div>
              <div class="form-title">修改后</div>
            </div>

            <div style="display: flex; flex-direction: column; padding: 64px 36px">
              <div
                class="form-item"
                style="display:flex;items-center;padding:8px;justify-content: space-between;"
                v-for="item in list"
              >
                <div class="form-label">{{ item.CHANNEL_NM }}</div>

                <div style="background-color: #eee; padding: 4px 8px">
                  {{ item.radioValue == "0" ? "ON" : "OFF" }}
                </div>
              </div>
            </div>
          </div>
        </div>
      </template>

      <div>
        <el-button size="small" style="margin-left: 12px" @click="isFirstSubmit = true">
          取消
        </el-button>
        <el-button
          size="small"
          type="primary"
          style="margin-left: 12px"
          @click="onSubmitForm"
        >
          提交
        </el-button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Prop, Watch } from "vue-property-decorator";

@Component
export default class CounterComponent extends Vue {
  // Prop 属性
  @Prop({ type: String, default: "Default Title" }) title!: string;

  // 后台数据列表
  list = [
    {
      CHANNEL_NM: "text1",
      CHANNEL_AUTH_FLG: "0",
      EDIT_STATUS: "0",

      radioValue: "0",
    },
    {
      CHANNEL_NM: "text2",
      CHANNEL_AUTH_FLG: "0",
      EDIT_STATUS: "1",

      radioValue: "0",
    },
    {
      CHANNEL_NM: "text3",
      CHANNEL_AUTH_FLG: "1",
      EDIT_STATUS: "0",

      radioValue: "1",
    },
    {
      CHANNEL_NM: "text4",
      CHANNEL_AUTH_FLG: "1",
      EDIT_STATUS: "0",

      radioValue: "1",
    },
    {
      CHANNEL_NM: "text5",
      CHANNEL_AUTH_FLG: "1",
      EDIT_STATUS: "0",

      radioValue: "1",
    },
    {
      CHANNEL_NM: "text6",
      CHANNEL_AUTH_FLG: "0",
      EDIT_STATUS: "1",

      radioValue: "0",
    },
    {
      CHANNEL_NM: "text7",
      CHANNEL_AUTH_FLG: "1",
      EDIT_STATUS: "0",

      radioValue: "1",
    },
    {
      CHANNEL_NM: "text8",
      CHANNEL_AUTH_FLG: "1",
      EDIT_STATUS: "1",

      radioValue: "1",
    },
  ];

  // 是否为第一次点击提交
  isFirstSubmit = true;

  // 点击提交按钮
  onSubmitForm() {
    if (this.isFirstSubmit) {
      this.isFirstSubmit = false;
    } else {
      // 第二次点击的逻辑 . 调用接口，处理
    }
  }
}
</script>

<style scoped>
.form-title {
  background-color: rgb(51, 51, 185);
  color: #fff;
  border: 1px solid #000;
  text-align: center;
  flex: 1;
}

.form-item {
  height: 36px;
  display: flex;
  align-items: center;
}
</style>

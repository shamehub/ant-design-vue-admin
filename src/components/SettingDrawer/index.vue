<template>
  <div>
    <a-drawer
      placement="right"
      :closable="false"
      :visible="visible"
      @close="onClose"
      width="300px"
    >
      <template v-slot:handle>
        <div class="handle" @click="visible = !visible">
          <a-icon :type="visible ? 'close' : 'setting'"></a-icon>
        </div>
      </template>
      <div>
        <template>
          <div>
            <h2>整体风格定制</h2>
            <a-radio-group
              :value="$route.query.navTheme || 'dark'"
              @change="e => handleSettingChange('navTheme', e.target.value)"
            >
              <a-radio value="dark">黑色</a-radio>
              <a-radio value="light">白色</a-radio>
            </a-radio-group>
            <h2>导航样式</h2>
            <a-radio-group
              :value="$route.query.navLayout || 'left'"
              @change="e => handleSettingChange('navLayout', e.target.value)"
            >
              <a-radio value="left">左边</a-radio>
              <a-radio value="right">右边</a-radio>
            </a-radio-group>
          </div>
        </template>
      </div>
    </a-drawer>
  </div>
</template>
<script>
export default {
  data() {
    return {
      visible: false
    };
  },
  methods: {
    onClose() {
      this.visible = false;
    },
    handleSettingChange(type, value) {
      this.$router.push({ query: { ...this.$route.query, [type]: value } });
    }
  }
};
</script>
<style scoped>
.handle {
  position: absolute;
  top: 240px;
  right: 300px;
  width: 48px;
  height: 48px;
  background: #1890ff;
  color: white;
  font-size: 20px;
  line-height: 48px;
  text-align: center;
  border-radius: 3px 0 0 3px;
}
</style>

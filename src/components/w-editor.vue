<template>
  <div>
    <div class="editor" :id="this.editId" :style="{ width : width+'px' }"></div>
  </div>
</template>

<script>
import wangEditor from 'wangeditor';
export default {
  name: "w-editor",
  model : { event:'change',prop :'content' },
  props : {
    content : { type :String, default : '' },
    editId : { type :String, default: '' },
    height : { type :[String,Number], default:450 },
    width : { type :[String,Number], default:750 },
    placeholder : { type :String, default :'请填写内容' },
  },
  mounted() {
    if(this.editor){
      this.init();
    }
  },
  computed: {
    editor() {
      return new wangEditor('#'+this.editId);
    }
  },
  watch: {
    content(newValue) {
      if (newValue != this.editor.txt.html()) {
        this.editor.txt.html(newValue)
      }
    }
  },
  methods: {
    init : function (){
      let that = this;
      this.editor.config.zIndex = 999;
      this.editor.config.height = this.height;
      this.editor.config.uploadImgShowBase64 = false;
      this.editor.config.placeholder = this.placeholder;
      this.editor.config.onchange = function (html){
        that.$emit('change',html);
      }
      this.editor.config.onblur = function (html){
        that.$emit('change',html);
      }
      this.editor.config.onfocus = function (html){
        that.$emit('change',html);
      }
      this.editor.create('#'+this.editId);
      this.editor.txt.html(this.content);
    },
  },
}
</script>

<style scoped>

</style>
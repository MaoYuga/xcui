<template lang="md">
## Modal 模态窗口

### 使用场景
> 模拟浏览器的 **alert**、**confirm**和**prompt**

### Demo

<demo>
    <example title="基础使用">
        <button class="btn btn-default" @click="this.modal1 = true">显示对话框</button>
        <xcui-modal
        :show.sync="modal1"
        title="基础弹窗"
        :on-ok="modal1OK">
        <div>XCUI，做有品质的外卖UI</div>
        </xcui-modal>
        <div>通过控制show来显示/隐藏对话框，需要将show设置为.sync双向绑定</div>
    </example>
    <example title="定义元素的显示">
        <button class="btn btn-default" @click="this.modal2 = true">自定义页头</button>
        <button class="btn btn-default" @click="this.modal3 = true">不带标题栏</button>
        <button class="btn btn-default" @click="this.modal4 = true">不带关闭按钮</button>
        <button class="btn btn-default" @click="this.modal5 = true">不带页脚</button>
        <button class="btn btn-default" @click="this.modal6 = true">不带关闭按钮和页脚</button>
        <xcui-modal
        :show.sync="modal2"
        title="自定义页头（有slot则无效）">
        <span slot="header" class="xcui-modal-demo-title">不一样的页头</span>
        <div>我跟你不一样，我有你没有的头脑</div>
        </xcui-modal>
        <xcui-modal
        :show.sync="modal3"
        :show-header="false">
        <div>无头骑士。生前是一名勇猛的骑士，由于在战场上不幸阵亡，首级被敌人割去，因此每逢月黑风高的夜晚他便会骑着一匹同为亡灵的马出没于沉睡谷，四处寻找自己遗失的首级；而每当看见与自己生前长相相似者便会斩其头颅带回。</div>
        </xcui-modal>
        <xcui-modal
        :show.sync="modal4"
        title="不带关闭按钮"
        :show-close-button="false">
        <div>不带关闭按钮</div>
        </xcui-modal>
        <xcui-modal
        :show.sync="modal5"
        title="不带页脚"
        :show-footer="false">
        <div>即使我失去了双脚，我依然顶天立地</div>
        </xcui-modal>
        <xcui-modal
        :show.sync="modal6"
        :show-close-button="false"
        :show-footer="false">
        <div>我且问你，除了刷新，你能如何关闭我？</div>
        </xcui-modal>
        <div>Modal提供了灵活的组件化API和Slot，可以自由控制整个Modal的组成部分。比如，页头、页脚和关闭按钮</div>
    </example>
    <example title="自定义样式">
        <button class="btn btn-default" @click="this.modal7 = true">Full对话框</button>
        <button class="btn btn-default" @click="this.modal8 = true">Small对话框</button>
        <button class="btn btn-default" @click="this.modal9 = true">自定义Style</button>
        <button class="btn btn-default" @click="this.modal10 = true">自定义class-name</button>
        <xcui-modal
        :show.sync="modal7"
        :size="'full'"
        title="Full对话框">
        <div>心宽体肥，宅心仁厚。</div>
        </xcui-modal>
        <xcui-modal
        :show.sync="modal8"
        :size="'small'"
        title="Small对话框">
        <div>即使我小，这世间也会有我的一席之地。因为我小巧玲珑，精灵剔透。</div>
        </xcui-modal>
        <xcui-modal
        :show.sync="modal9"
        :style="{'transform': 'rotate(-10deg)'}"
        title="自定义Style">
        <div>身正不怕影子斜</div>
        </xcui-modal>
        <xcui-modal
        :show.sync="modal10"
        title="自定义class-name"
        :class-name="'xcui-modal-demo-class'">
        <div>欲与天公试比高</div>
        </xcui-modal>
        <style>
        .xcui-modal-demo-class { top: 0; }
        </style>
        <div>通过设置size可以快速设置对话框的宽度大小，也可以设置class-name和style自定义Modal的样式</div>
    </example>
</demo>

## Props
| 名字 | 类型 | 默认 | 描述 | 是否必选 |
|-----|-----|-----|-----|----|
|show|Boolean|false|对话框是否显示,需要.sync双向绑定|**必选**|
|title|String|-|对话框的标题，如果slot定义了header，则title无效|可选|
|mask-closable|Boolean|true|是否允许点击遮罩层关闭对话框|可选|
|show-close-button|Boolean|true|是否显示右上角的关闭按钮|可选|
|show-header|Boolean|true|是否显示整个标题栏|可选|
|show-footer|Boolean|true|是否显示整个底边栏|可选|
|ok-text|String|确定|确定按钮的文字|可选|
|cancel-text|String|取消|取消按钮的文字|可选|
|size|String|middle|预设对话框浮层的宽度大小。可选值：small/middle/large/full|可选|
|class-name|String|-|自定义样式类名|可选|
|style|object|-|设置对话框浮层的样式，调整浮层位置等。该属性设置的是.xcui-modal的样式|可选|

## Events
| 名字 | 描述 | 是否必选 |
|-----|-----|----|
|on-ok|点击确定的回调函数。回调函数如果返回真值(true)，则不再关闭对话框；如果返回假值(false)或不返回，则默认执行on-ok后关闭对话框|可选|
|on-cancel|点击取消和右上角关闭的回调函数。回调函数如果返回真值(true)，则不再关闭对话框；如果返回假值(false)或不返回，则默认执行on-cancel后关闭对话框|可选|

## Slot
| 名字 | 描述 |
|-----|-----|
|header|自定义页头|
|footer|自定义页脚内容|
|close|自定义右上角关闭按钮|
|-|对话框的主体内容|

</template>
<script>
import xcuiModal from '../components/modal';

let ModalDemo = {
    components: {
        xcuiModal
    },
    data() {
        return {
            modal1: false,
            modal2: false,
            modal3: false,
            modal4: false,
            modal5: false,
            modal6: false,
            modal7: false,
            modal8: false,
            modal9: false,
            modal10: false
        };
    },
    methods: {
        modal1OK() {
            console.log('modal1OK');
        }
    }
};

export default ModalDemo;
</script>
<style lang="less" scoped>
.xcui-modal-demo-title {
    color: #66ccff;
}
</style>

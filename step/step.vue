<template>
  <div class="vux-step">
    <slot></slot>
  </div>
</template>

<script>
  export default {
    props: {
      current: Number,
      backgroundColor: {
        type: String,
        default: '#fff'
      },
      gutter: {
        type: String,
        default: '10px'
      }
    },
    mounted () {
    this._mapPropsToChildComponent()
  },
  watch: {
    current () {
      this._mapPropsToChildComponent()
    }
  },
  methods: {
    _mapPropsToChildComponent () {
      const _this = this
      const len = this.$children.length - 1
      this.$children.forEach((child, index) => {
        child.props_stepNumber = (index + 1).toString()
      child.props_stepLast = index === len
      if (index === _this.current) {
        child.props_status = 'process'
      } else if (index < _this.current) {
        child.props_status = 'finish'
      } else {
        child.props_status = 'wait'
      }
    })
    }
  }
  }
</script>

<style>
  .vux-step {
    /*display: flex;*/
    background-color: #fff;
    padding: 20px 0;
  }
  .vux-step-item {
    /*display: block;*/
    display: flex;
    position: relative;
    overflow: hidden;
  }
  .vux-step-item-with-tail {
    /*flex: 1;*/
    padding-bottom: 10px;
  }
  .vux-step-item-tail {
    width: 1px;
    height: 200px;
    position: absolute;
    left: 28px;
    top: 10px;
    padding: 0 0;
    transition: all 0.4s ease 0s;
  }
  .vux-step-item-tail-finish {
    background: #09bb07 none repeat scroll 0 0;
  }
  .vux-step-item-tail-process, .vux-step-item-tail-wait {
    background: #CCC none repeat scroll 0 0;
  }
  .vux-step-item-checked:before {
    font-size: 15px;
    transform: translateY(-10%);
  }
  .vux-step-item-title {
    width: 100%;
    display: inline-block;
    font-size: 1.4rem;
    height: 25px;
    border-bottom: 1px solid #d0d0d0
  }
  .vux-step-item-title i {
    position: absolute;
    right: 20px;
  }
  .vux-step-item-value{
    padding-top: 10px;
  }
  .vux-step-item-value p{
    margin: 0;
  }
  .vux-step-item-head {
    position: relative;
    display: inline-block;
    margin: 0 -4px 0 18px;
    flex: 1;
  }
  .vux-step-item-icon, .vux-step-item-icon i:before{
    font-size: 1.2rem;
  }
  .vux-step-item-head-inner {
    width: 20px;
    height: 20px;
    border-radius: 99px;
    text-align: center;
    font-size: 0.9rem;
    transition: all 0.4s ease 0s;
    background: #fff none repeat scroll 0 0;
  }
  .vux-step-item-head-finish .vux-step-item-head-inner{
    border: 1px solid #09bb07;
    color: #09bb07;
  }
  .vux-step-item-head-process .vux-step-item-head-inner{
    border: 1px solid #09bb07;
    color: #FFF;
    background: #09bb07 none repeat scroll 0 0;
  }
  .vux-step-item-head-wait .vux-step-item-head-inner {
    border: 1px solid #888;
    color: #888;
  }
  .vux-step-item-main {
    width: 90%;
    display: inline-block;
    position: relative;
    vertical-align: top;
    color: #888;
    padding-left: 20px;
    padding-right: 20px;
    flex: 12;
    background-color: #fff;
  }
  .vux-step-item-main-process {
    font-weight: bold;
    color: #666;
  }
  .step-item-move-enter-active {
    position: relative;
    animation: move-in .5s;
  }
  .step-item-move-leave-active {
    position: relative;
    animation: move-out .5s;
  }
  @keyframes move-in {
    0% {
      opacity: 0;
      -webkit-transform: translate3d(0, -10%, 0);
      transform: translate3d(0, -10%, 0);
    }
    100% {
      opacity: 1;
      -webkit-transform: translate3d(0, 0, 0);
      transform: translate3d(0, 0, 0);
    }
  }
  @keyframes move-out {
    0% {
      opacity: 1;
      -webkit-transform: translate3d(0, -10%, 0);
      transform: translate3d(0, -10%, 0);
    }
    100% {
      opacity: 0;
      -webkit-transform: translate3d(0, 0, 0);
      transform: translate3d(0, 0, 0);
    }
  }

</style>
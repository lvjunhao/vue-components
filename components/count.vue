<template>
    <span class="animatenum"></span>
</template>

<script>
import '../pages/css/count.css'
export default {
  data() {
    return {};
  },
  props: ["start", "end", "duration", "id"],
  watch: {
    end: function(n, o) {
      this.animateNum(n);
    }
  },
  mounted() {
    var originNum = this.end;
    this.animateNum(originNum);
  },
  methods: {
    animateNum: function(n) {
      var cc =
        "<span class='num-box'><span class='num'>0</span><span class='num'>1</span><span class='num'>2</span><span class='num'>3</span><span class='num'>4</span><span class='num'>5</span><span class='num'>6</span><span class='num'>7</span><span class='num'>8</span><span class='num'>9</span><span class='num symbol'>,</span><span class='num symbol'>.</span></span>";
      var str = String(n);
      for (var i = 0; i < str.length; i++) {
        var curLength = this.$el.querySelectorAll("span.num-area").length;
        if (str.length > curLength) {
          var span = document.createElement("span");
          span.className = "num-area";
          span.innerHTML = cc;
          this.$el.appendChild(span);
        }
        var a = str[i];
        if (a == ",") {
          a = 10;
        } else if (a == ".") {
          a = 11;
        } else {
          a = parseInt(a);
        }
        // 此处0.36666667应该与实际数字容器高度相等
        var mtop = -a * 44 + "px";
        var j = i + 1;
        this.$el
          .querySelectorAll("span.num-area:nth-child(" + j + ")")[0]
          .setAttribute("num", j);
        
        var parentArea=this.$el
          .querySelectorAll("span.num-area:nth-child(" + j + ")")[0];
        
        if(a==10||a==11){
          parentArea.className="num-area symbol";
                  }else{
          parentArea.className="num-area";
        }
          parentArea.querySelector(".num-box").style.transform =
          "translateY(" + mtop + ")";
      }
    }
  }
};
</script>


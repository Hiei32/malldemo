<template>
  <div class="category">
    <div>
      <h1>分类</h1>
      <h2>测试better-scroll组件</h2>
      <div onclick="alert('点击了')">测试点击</div>
      <ul>
        <li>测试1</li>
        <li>测试2</li>
        <li>测试3</li>
        <li>测试4</li>
        <li>测试5</li>
        <li>测试6</li>
        <li>测试7</li>
        <li>测试8</li>
        <li>测试9</li>
        <li>测试10</li>
        <li>测试11</li>
        <li>测试12</li>
        <li>测试13</li>
        <li>测试14</li>
        <li>测试15</li>
        <li>测试16</li>
        <li>测试17</li>
        <li>测试18</li>
        <li>测试19</li>
        <li>测试20</li>
        <li>测试21</li>
        <li>测试22</li>
        <li>测试23</li>
        <li>测试24</li>
        <li>测试25</li>
        <li>测试26</li>
        <li>测试27</li>
        <li>测试28</li>
        <li>测试29</li>
        <li>测试30</li>
        <li>测试31</li>
        <li>测试32</li>
        <li>测试33</li>
        <li>测试34</li>
        <li>测试35</li>
        <li>测试36</li>
        <li>测试37</li>
        <li>测试38</li>
        <li>测试39</li>
        <li>测试40</li>
        <li>测试41</li>
        <li>测试42</li>
        <li>测试43</li>
        <li>测试44</li>
        <li>测试45</li>
        <li>测试46</li>
        <li>测试47</li>
        <li>测试48</li>
        <li>测试49</li>
        <li>测试50</li>
        <li>测试51</li>
        <li>测试52</li>
        <li>测试53</li>
        <li>测试54</li>
        <li>测试55</li>
        <li>测试56</li>
        <li>测试57</li>
        <li>测试58</li>
        <li>测试59</li>
        <li>测试60</li>
        <li>测试61</li>
        <li>测试62</li>
        <li>测试63</li>
        <li>测试64</li>
        <li>测试65</li>
        <li>测试66</li>
        <li>测试67</li>
        <li>测试68</li>
        <li>测试69</li>
        <li>测试70</li>
        <li>测试71</li>
        <li>测试72</li>
        <li>测试73</li>
        <li>测试74</li>
        <li>测试75</li>
        <li>测试76</li>
        <li>测试77</li>
        <li>测试78</li>
        <li>测试79</li>
        <li>测试80</li>
        <li>测试81</li>
        <li>测试82</li>
        <li>测试83</li>
        <li>测试84</li>
        <li>测试85</li>
        <li>测试86</li>
        <li>测试87</li>
        <li>测试88</li>
        <li>测试89</li>
        <li>测试90</li>
        <li>测试91</li>
        <li>测试92</li>
        <li>测试93</li>
        <li>测试94</li>
        <li>测试95</li>
        <li>测试96</li>
        <li>测试97</li>
        <li>测试98</li>
        <li>测试99</li>
        <li>测试100</li>
      </ul>
    </div>
  </div>
</template>

<script>
import BScroll from "better-scroll";
export default {
  name: "Category",
  data() {
    return {
      cate: null,
    };
  },
  mounted() {
    this.cate = new BScroll(".category", {
      //probeType侦测滚动
      //0和1都是不侦测
      //2手指滚动的过程中侦测，手指离开后的惯性过程不侦测
      //3只要是滚动，都侦测
      probeType: 3,
      //阻止滚动中内部元素的点击事件
      click: false,
      pullUpLoad: true,
      //鼠标滚轮
      mouseWheel: true,
    });
    this.cate.on("scroll", (position) => {
      //console.log(position);
    });
    this.cate.on("pullingUp", () => {
      console.log("上拉加载更多");
      //在这里可以发送网络请求，请求更多页的数据
      //等数据请求完成，等新数据请求完成后
      setTimeout(() => {
        this.cate.finishPullUp();
      }, 2000);
    });
  },
};
</script>

<style lang="scss" scoped>
.category {
  width: 100%;
  height: 400px;
  background: #eee;
  overflow: hidden;
}
</style>
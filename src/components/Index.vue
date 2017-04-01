<template>
  <div class="page has-navbar" v-nav="{ title: '麻花 & 谢羊羊', showMenuButton: true, onMenuButtonClick: onMenuButtonClick}">
    <div class="page-content text-center" style="padding-top: 43px;background: #163553;">

      <div class="body">
      
        <div class="countdown-table">
          <h2 style="color:#ffffff;font-weight:200">已经在一起</h2>
          <div class="simply-countdown simply-countdown-one">
            <div class="simply-section simply-days-section">
              <div>
                <span class="simply-amount">{{days}}</span><span class="simply-word">天</span>
              </div>
            </div>
            <div class="simply-section simply-hours-section">
              <div>
                <span class="simply-amount">{{hours}}</span><span class="simply-word">时</span>
              </div>
            </div>
            <div class="simply-section simply-minutes-section">
              <div>
                <span class="simply-amount">{{mins}}</span><span class="simply-word">分</span>
              </div>
            </div>
            <div class="simply-section simply-seconds-section">
              <div>
                <span class="simply-amount">{{seconds}}</span><span class="simply-word">秒</span>
              </div>
            </div>
          </div>
           
        </div>

      </div>

    </div>
  </div>
</template>
<script>

  export default {

    ready () {

    },

    data () {
      return {
        days: 0,
        hours: 0,
        mins: 0,
        seconds: 0
      }
    },

    mounted () {

      var gapTime = () => {

        var startTime = '2017-02-15';  
        var endTime = new Date();
        var gapTimestamp = endTime.getTime() - new Date(2017, 1, 15, 0, 0, 0).getTime();        

        //计算出相差天数  
        var days=Math.floor(gapTimestamp/(24*3600*1000));
    
        //计算出小时数  
        var leave1=gapTimestamp%(24*3600*1000);
        var hours=Math.floor(leave1/(3600*1000));

        //计算相差分钟数  
        var leave2=leave1%(3600*1000);        //计算小时数后剩余的毫秒数  
        var minutes=Math.floor(leave2/(60*1000));

        //计算相差秒数  
        var leave3=leave2%(60*1000);      //计算分钟数后剩余的毫秒数  
        var seconds=Math.round(leave3/1000);

        return {
          days,
          minutes,
          hours,
          seconds
        }

      }

      var gap = () => {
        var gap = gapTime();

        this.days = gap.days;
        this.hours = gap.hours;
        this.mins = gap.minutes;
        this.seconds = gap.seconds;
      }

      gap();

      setInterval(() => {
        gap();
      }, 1000);

    },

    methods: {

      onMenuButtonClick () {
        location.hash = 'about';
      }

    }

  }
</script>
<style>
  h2 {
    font-family: Candara,Calibri,Segoe,Segoe UI,Optima,Arial,sans-serif;
    color: #888;
  }

  .page.has-navbar .page-content {
    padding-top: 100px;
  }

  .item-note.left {
    float: left!important;
    text-align: left;
  }

  .item-note {
    text-overflow:ellipsis!important;
    white-space: nowrap!important;
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-line-clamp: 3;
    overflow: hidden;
    width: 100%;
  }

  .body {
    padding: 15px;
  }

  .simply-countdown {
    margin-top: 3em;
    margin-bottom: 3em;
  }

  .simply-countdown > .simply-section {
    display: table-cell;
    width: 110px;
    height: 120px;
    background: rgba(0, 0, 0, 0.2);
    border-bottom: 4px solid rgba(250, 70, 89, 0.5);
    margin: 0px 7px;
    position: relative;
    animation: pulse 1.01s ease infinite;
  }

  @keyframes pulse {
    0% {
      transform: scale(1);
    }
    50% {
      transform: scale(1.03);
    }
    100% {
      transform: scale(1);
    }
  }
  .simply-countdown > .simply-section > div {
    display: table-cell;
    vertical-align: middle;
    height: 100px;
    width: 110px;
  }

  .simply-countdown > .simply-section .simply-amount,
  .simply-countdown > .simply-section .simply-word {
    display: block;
    color: white;
  }

  .simply-countdown > .simply-section .simply-amount {
    font-size: 40px;
    line-height: 80px;
  }

  .simply-countdown > .simply-section .simply-word {
    color: rgba(255, 255, 255, 0.7);
    text-transform: uppercase;
    font-size: 12px;
  }

  body {
    font-family: "Work Sans", Arial, sans-serif;
    font-weight: 400;
    font-size: 16px;
    line-height: 1.7;
    color: #828282;
    background: #fff;
  }

  .countdown-table {
    display: table;
    margin: 0 auto;
  }

  .body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
  }

</style>

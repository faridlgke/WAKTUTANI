<template>
  <!-- Main content -->
  <section class="content">
    <!-- GitHub hint -->
    <div class="row">
      <div class="col-xs-12">
        <alert :dismissible="true"
               type="success"
               :iconClasses="['fa', 'fa-check']"
               title="WAKTUTANI is open source! - (COMPETITION PERIOD)">
          <span>Click Icon for Waktutani github.</span>
          <a href="https://github.com/" target="_blank">
            <i class="fa fa-github fa-2x"></i>
          </a>
        </alert>
      </div>

      <!-- Info boxes -->
      <h4 style="font-weight: bold; margin-left: 14px;">AREA WITH RICE NEEDS</h4>
      <div class="col-md-3 col-sm-6 col-xs-12">
        <info-box color-class="bg-aqua"
                  :icon-classes="['warning']"
                  text="KABUPATEN PANGANDARAN"
                  number="-11.200 TON">
          <img src="../../assets/bdg_kab.jpg" style="max-width: 40px;" alt="">          
        </info-box>
      </div>
      <!-- /.col -->
      <div class="col-md-3 col-sm-6 col-xs-12">
        <info-box color-class="bg-red"
                  :icon-classes="[]"
                  text="KABUPATEN KUNINGAN"
                  number="-10.410 TON"></info-box>
      </div>
      <!-- /.col -->

      <!-- fix for small devices only -->
      <div class="clearfix visible-sm-block"></div>
      
      <div class="col-md-3 col-sm-6 col-xs-12">
        <info-box color-class="bg-green"
                  :icon-classes="[]"
                  text="KABUPATEN CIAMIS"
                  number="-9.800 TON"></info-box>
      </div>
      <!-- /.col -->
      <div class="col-md-3 col-sm-6 col-xs-12">
        <info-box color-class="bg-yellow"
                  :icon-classes="['1']"
                  text="KABUPATEN SUMEDANG" 
                  number="-7.233 TON"></info-box>
      </div>
      <!-- /.col -->
    </div>
    <!-- /.row -->

    <div class="col-xs-12">
      <div class="box">
        <div class="box-header with-border">
          <h3 class="box-title"></h3>
          <div class="box-body">
            <div class="col-sm-6 col-xs-12">
              <p class="text-center">
                <strong>TOTAL NEEDS VS TOTAL PRODUCTION IN PANGANDARAN</strong>
              </p>
              <canvas id="trafficBar" ></canvas>
              <br>
              <p class="text-center">
                <strong>TOTAL NEEDS VS TOTAL PRODUCTION IN SUKABUMI</strong>
              </p>  
              <canvas id="trafficBar2" ></canvas>
            </div>
            <hr class="visible-xs-block">
            <div class="col-sm-6 col-xs-12">
              <p class="text-center">
                <strong>TOTAL NEEDS/TOTAL PRODUCTION IN KUNINGAN</strong>
              </p>
              <canvas id="trafficBar3"></canvas>
              <p class="text-center">
                <strong>TOTAL NEEDS VS TOTAL PRODUCTION IN SUMEDANG</strong>
              </p>  
              <canvas id="trafficBar4"></canvas>
            </div>
          </div>
        </div>
        <div class="text-center">
          <small><b>Pro Tip</b> Don't forget to vote for WAKTUTANI!</small>
        </div>
      </div>
    </div>
    <!-- /.row -->

    <!-- Main row -->
    <div class="row">
      <div class="col-md-3 col-sm-6 col-xs-12">
        <process-info-box color-class="bg-yellow"
                          :icon-classes="['ion', 'ion-ios-pricetag-outline']"
                          text=""
                          number="Planting Calender for Your City Here"
                          :progress="50"
                          description="Plan it carefully!"></process-info-box>
      </div>
      <!-- /.col -->
      <div class="col-md-3 col-sm-6 col-xs-12">
        <process-info-box color-class="bg-green"
                          :icon-classes="['ion', 'ion-ios-heart-outline']"
                          text=""
                          number="Join the Same Profession Community Here"
                          :progress="20"
                          description="Face your problem together"></process-info-box>
      </div>
      <!-- /.col -->
      <div class="col-md-3 col-sm-6 col-xs-12">
        <process-info-box color-class="bg-red"
                          :icon-classes="['ion', 'ion-ios-cloud-download-outline']"
                          text=""
                          number="Statistics"
                          :progress="70"
                          description="Check the demands"></process-info-box>
      </div>
      <!-- /.col -->
      <div class="col-md-3 col-sm-6 col-xs-12">
        <process-info-box color-class="bg-aqua"
                          :icon-classes="['ion', 'ion-ios-chatbubble-outline']"
                          text=""
                          number="Consultation with the professional"
                          :progress="40"
                          description="Finding Solution on your problem"></process-info-box>
      </div>
      <!-- /.col -->
    </div>
    <!-- /.row -->
  </section>
  <!-- /.content -->
</template>

<script>
import Chart from 'chart.js'
import Alert from '../widgets/Alert'
import InfoBox from '../widgets/InfoBox'
import ProcessInfoBox from '../widgets/ProcessInfoBox'

export default {
  name: 'Dashboard',
  components: {
    Alert,
    InfoBox,
    ProcessInfoBox
  },
  data () {
    return {
      generateRandomNumbers (numbers, max, min) {
        var a = []
        for (var i = 0; i < numbers; i++) {
          a.push(Math.floor(Math.random() * (max - min + 1)) + max)
        }
        return a
      }
    }
  },
  computed: {
    coPilotNumbers () {
      return this.generateRandomNumbers(12, 1000000, 10000)
    },
    personalNumbers () {
      return this.generateRandomNumbers(12, 1000000, 10000)
    },
    isMobile () {
      return (window.innerWidth <= 800 && window.innerHeight <= 600)
    }
  },
  mounted () {
    this.$nextTick(() => {
      var ctx = document.getElementById('trafficBar').getContext('2d')
      var config = {
        type: 'line',
        data: {
          labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
          datasets: [{
            label: 'RICE PRODUCTION',
            fill: false,
            borderColor: '#284184',
            pointBackgroundColor: '#284184',
            backgroundColor: 'rgba(0, 0, 0, 0)',
            data: [
              6113.81,
              14778.42,
              29941.48,
              24212.32,
              16802.86,
              16924.33,
              20669.54,
              17855.57,
              16863.59,
              10547.34,
              9433.9,
              9008.76
            ]
          }, {
            label: 'TOTAL NEEDS',
            borderColor: '#4BC0C0',
            pointBackgroundColor: '#4BC0C0',
            backgroundColor: 'rgba(0, 0, 0, 0)',
            data: [
              47667.44,
              52774.67,
              51072.26,
              52774.67,
              51072.26,
              52774.67,
              52774.67,
              51072.26,
              52774.67,
              51072.26,
              52774.67,
              52516.73
            ]
          }]
        },
        options: {
          responsive: true,
          maintainAspectRatio: !this.isMobile,
          legend: {
            position: 'bottom',
            display: true
          },
          tooltips: {
            mode: 'label',
            xPadding: 10,
            yPadding: 10,
            bodySpacing: 10
          },
          scales: {
            xAxes: [{
              display: true,
              scaleLabel: {
                display: true,
                labelString: 'Months'
              }
            }],
            yAxes: [{
              display: true,
              scaleLabel: {
                display: true,
                labelString: 'Weigth (ton)'
              }
            }]
          }
        }
      }
      new Chart(ctx, config) // eslint-disable-line no-new
      var ctx2 = document.getElementById('trafficBar2').getContext('2d')
      var config2 = {
        type: 'line',
        data: {
          labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
          datasets: [{
            label: 'RICE PRODUCTION',
            fill: false,
            borderColor: '#284184',
            pointBackgroundColor: '#284184',
            backgroundColor: 'rgba(0, 0, 0, 0)',
            data: [
              9309.19,
              22502.36,
              45590.39,
              36866.87,
              25584.87,
              25769.82,
              31472.47,
              27187.78,
              25677.35,
              16059.9,
              14364.52,
              13717.19
            ]
          }, {
            label: 'TOTAL NEEDS',
            borderColor: '#4BC0C0',
            pointBackgroundColor: '#4BC0C0',
            backgroundColor: 'rgba(0, 0, 0, 0)',
            data: [
              21818.57,
              19707.09,
              21818.57,
              21114.74,
              21818.57,
              21114.74,
              21818.57,
              21818.57,
              21114.74,
              21818.57,
              21114.74,
              21818.57
            ]
          }]
        },
        options: {
          responsive: true,
          maintainAspectRatio: !this.isMobile,
          legend: {
            position: 'bottom',
            display: true
          },
          tooltips: {
            mode: 'label',
            xPadding: 10,
            yPadding: 10,
            bodySpacing: 10
          },
          scales: {
            xAxes: [{
              display: true,
              scaleLabel: {
                display: true,
                labelString: 'Months'
              }
            }],
            yAxes: [{
              display: true,
              scaleLabel: {
                display: true,
                labelString: 'Weigth (ton)'
              }
            }]
          }
        }
      }
      new Chart(ctx2, config2) // eslint-disable-line no-new
      var ctx3 = document.getElementById('trafficBar3').getContext('2d')
      var config3 = {
        type: 'line',
        data: {
          labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
          datasets: [{
            label: 'RICE PRODUCTION',
            fill: false,
            borderColor: '#284184',
            pointBackgroundColor: '#284184',
            backgroundColor: 'rgba(0, 0, 0, 0)',
            data: [
              4368.05,
              10558.54,
              21391.9,
              17298.65,
              12004.92,
              12091.7,
              14767.5,
              12757.03,
              12048.31,
              7535.62,
              6740.11,
              6436.37
            ]
          }, {
            label: 'TOTAL NEEDS',
            borderColor: '#4BC0C0',
            pointBackgroundColor: '#4BC0C0',
            backgroundColor: 'rgba(0, 0, 0, 0)',
            data: [
              9561.64,
              8636.32,
              9561.64,
              9253.2,
              9561.64,
              9253.2,
              9561.64,
              9561.64,
              9253.2,
              9561.64,
              9253.2,
              9561.64
            ]
          }]
        },
        options: {
          responsive: true,
          maintainAspectRatio: !this.isMobile,
          legend: {
            position: 'bottom',
            display: true
          },
          tooltips: {
            mode: 'label',
            xPadding: 10,
            yPadding: 10,
            bodySpacing: 10
          },
          scales: {
            xAxes: [{
              display: true,
              scaleLabel: {
                display: true,
                labelString: 'Months'
              }
            }],
            yAxes: [{
              display: true,
              scaleLabel: {
                display: true,
                labelString: 'Weigth (ton)'
              }
            }]
          }
        }
      }
      new Chart(ctx3, config3) // eslint-disable-line no-new
      var ctx4 = document.getElementById('trafficBar4').getContext('2d')
      var config4 = {
        type: 'line',
        data: {
          labels: ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
          datasets: [{
            label: 'RICE PRODUCTION',
            fill: false,
            borderColor: '#284184',
            pointBackgroundColor: '#284184',
            backgroundColor: 'rgba(0, 0, 0, 0)',
            data: [
              6010.7,
              14529.18,
              29436.52,
              23803.98,
              16519.48,
              16638.9,
              20320.95,
              17554.44,
              16579.19,
              10369.46,
              9274.79,
              8856.83
            ]
          }, {
            label: 'TOTAL NEEDS',
            borderColor: '#4BC0C0',
            pointBackgroundColor: '#4BC0C0',
            backgroundColor: 'rgba(0, 0, 0, 0)',
            data: [
              10195.03,
              9208.41,
              10195.03,
              9866.16,
              10195.03,
              9866.16,
              10195.03,
              10195.03,
              9866.16,
              10195.03,
              9866.16,
              10195.03
            ]
          }]
        },
        options: {
          responsive: true,
          maintainAspectRatio: !this.isMobile,
          legend: {
            position: 'bottom',
            display: true
          },
          tooltips: {
            mode: 'label',
            xPadding: 10,
            yPadding: 10,
            bodySpacing: 10
          },
          scales: {
            xAxes: [{
              display: true,
              scaleLabel: {
                display: true,
                labelString: 'Months'
              }
            }],
            yAxes: [{
              display: true,
              scaleLabel: {
                display: true,
                labelString: 'Weigth (ton)'
              }
            }]
          }
        }
      }
      new Chart(ctx4, config4) // eslint-disable-line no-new
      var pieChartCanvas = document.getElementById('languagePie').getContext('2d')
      var pieConfig = {
        type: 'doughnut',
        data: {
          labels: ['Kabupaten Sukabumi', 'Kabupaten Pangandaran', 'Kota Subang'],
          datasets: [{
            data: [56.6, 37.7, 4.1],
            backgroundColor: ['#00a65a', '#f39c12', '#00c0ef'],
            hoverBackgroundColor: ['#00a65a', '#f39c12', '#00c0ef']
          }]
        },
        options: {
          responsive: true,
          maintainAspectRatio: !this.isMobile,
          legend: {
            position: 'bottom',
            display: true
          }
        }
      }

      new Chart(pieChartCanvas, pieConfig) // eslint-disable-line no-new
    })
  }
}
</script>
<style>
.info-box {
  cursor: pointer;
}
.info-box-content {
  text-align: center;
  vertical-align: middle;
  display: inherit;
}
.fullCanvas {
  width: 100%;
}
</style>

---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
title: 랭킹
icon: fa fa-line-chart
permalink: ranking.html
cloudjs:
  - //cdn.jsdelivr.net/npm/chart.js@2.7.2/dist/Chart.bundle.min.js
  - //cdn.jsdelivr.net/npm/chartjs-plugin-datalabels@0.3.0
---

# 공식 랭킹

| 회차          | 순위               | 등락   | 득표 및 비고 |
|:-------------|:------------------|:------|:----------|
| 2018-08-11   | 6               | 2차순위 대비 <span style="color:rgba(255,99,132,1)"><i class="fa fa-arrow-circle-up" aria-hidden="true" alt="상승" ></i> 16</span> | 30명, 속보 / 안준영 -_- |
| 2018-08-07   | 6               | 2차순위 대비 <span style="color:rgba(255,99,132,1)"><i class="fa fa-arrow-circle-up" aria-hidden="true" alt="상승" ></i> 16</span> | 30명, 속보 / 안준영 -_- |
| 8            | 22               | <span style="color:rgba(255,99,132,1)"><i class="fa fa-arrow-circle-up" aria-hidden="true" alt="상승" ></i> 14</span> | 30명, 2차 순위발표 / 남성 6위 / 562,216표 |
| 7            | 순위 미공개          |       | 현장 투표 / 댄스 16등 / 369표        |
| 6            | 순위 미공개          |       |                       |
| 5            | 36                | <span style="color:rgba(255,99,132,1)"><i class="fa fa-arrow-circle-up" aria-hidden="true" alt="상승" ></i> 3</span>    | 58명, 1차 순위발표 / 160,881표  |
| 4            | 순위 미공개          |       |                       |
| 3            | 39                | <span style="color:rgba(255,99,132,1)"><i class="fa fa-arrow-circle-up" aria-hidden="true" alt="상승" ></i> 6</span>    | 96명, 현장 투표 / 116표        |
| 2            | 45                | <span style="color:rgba(54, 162, 235, 1)"><i class="fa fa-arrow-circle-down" aria-hidden="true" alt="하락" ></i> 4</span>    | 96명                    |
| 1            | 41                |       | 96명                    |

<canvas id="mnetChart" width="400" height="200"></canvas>

> 출처 : [엠넷 프로듀스48 프로필](http://produce48.mnet.com/pc/profile/23)



---

# 네이버 실시간 급상승 검색어

| 일자                     | 순위              |    비고    |
|:------------------------|:-----------------|:----------|
| 2018-07-28 (토) 00:55:00 | 8               | 7화 본방      |
| 2018-07-24 (화) 16:14:30 | 4               | 7화 직캠 선공개 |
| 2018-07-14 (토) 02:16:00 | 20              | 6화 본방      |
| 2018-07-07 (토) 02:13:00 | 17              | 5화 순위발표   |

**네이버 실시간 급상승 검색어**는 20위까지 노출된다 

> 출처 : [네이버 데이터랩](https://datalab.naver.com/keyword/realtimeSearch.naver?startDate=2017-03-29&endDate=2018-07-28&query=%EC%8B%9C%ED%83%80%EC%98%A4%20%EB%AF%B8%EC%9A%B0)

---

# 국프의 정원

| 일자            | 단계                     |    비고           |
|:---------------|:------------------------|:-----------------|
| 2018-08-10     | 4차 / 2단계               | 미정              |
| 2018-08-01     | 4차 / 1단계               | 9일              |
| **2018-08-01** | **3차 달성 / 11일**        | **미미박스**       |
| 2018-07-28     | 3차 / 3단계               | 04일              |
| 2018-07-24     | 3차 / 2단계               | 04일              |
| 2018-07-20     | 3차 / 1단계               | 04일              |
| **2018-07-20** | **2차 달성 / 17일**       | **MYCT 왕관세트**   |
| 2018-07-17     | 2차 / 3단계               | 03일              |
| 2018-07-13     | 2차 / 2단계               | 04일              |
| 2018-07-03     | 2차 / 1단계               | 10일              |
| **2018-07-03** | **1차 달성 / 44일**        | **칼로바이 워터젤리** |
| 2018-06-30     | 1차 / 3단계               | 03일              |
| 2018-06-23     | 1차 / 2단계               | 07일              |
| 2018-05-21     | 1차 / 1단계               | 33일              |

<canvas id="gardenChart" width="400" height="200"></canvas>

> 출처: [국프의 정원](https://produce48.kr/m48_detail.php?idx=31&cate=hug)

숫자 3 은 금지다

<script>
window.onload = function() {
    var mnetCtx = document.getElementById("mnetChart");
    var mnetChart = new Chart(mnetCtx, {
        type: 'bar',
        data: {
            labels: ["1회차", "2회차", "3회차", "4회차", "7회차", "08-07", "08-11"],
            datasets: [{
                type: 'line',
                label: '순위',
                fill: false,
                spanGaps: true,
                data: [41, 45, 39, 36, 22, 6, 6],
                backgroundColor: 'rgba(255, 99, 132, 0.2)',
                borderColor: 'rgba(255,99,132,1)',
                datalabels: {
                    align: 'end',
                    anchor: 'end',
                    formatter: function(value, context) {
                        return value + '위';
                    }
                }
            }]
        },
        options: {
            responsive: true,
            title: {
                display: false,
            },
            tooltips: {
            mode: 'index',
            intersect: true
            },
            scales: {
                yAxes: [{
                    type: 'linear',
                    position: 'left',
                    scaleLabel: {
                        display: false,
                    },
                    ticks: {
                        display: true,
/*
                        min: 1,
                        max: 96,
*/
                        reverse: true,
                        beginAtZero: false,
                    },
                    gridLines: {
                        drawOnChartArea: true
                    }
                }],
                xAxes: [{
                    ticks: {
                        beginAtZero:true,
                    }
                }]
            },
            plugins: {
                datalabels: {
                    backgroundColor: function(context) {
                        return context.dataset.backgroundColor;
                    },
                    borderRadius: 4,
                    formatter: Math.round,
                    font: {
                        weight: 'bold'
                    }
                }
            }
        }
    });

    var gardenCtx = document.getElementById("gardenChart");
    var gardenChart = new Chart(gardenCtx, {
        type: 'bar',
        data: {
            labels: ["1차", "2차", "3차", "4차", "5차"],
            datasets: [{
                type: 'bar',
                label: '1단계',
                data: [33, 10, 4, 9, NaN],
                backgroundColor: 'rgba(54, 162, 235, 0.2)',
                borderColor: 'rgba(54, 162, 235, 1)',
    /*
                backgroundColor: [
                    'rgba(255, 99, 132, 0.2)',
                    'rgba(54, 162, 235, 0.2)',
                    'rgba(255, 206, 86, 0.2)',
                    'rgba(75, 192, 192, 0.2)',
                    'rgba(153, 102, 255, 0.2)',
                ],
                borderColor: [
                    'rgba(255,99,132,1)',
                    'rgba(54, 162, 235, 1)',
                    'rgba(255, 206, 86, 1)',
                    'rgba(75, 192, 192, 1)',
                    'rgba(153, 102, 255, 1)',
                ]
    */            
            },{
                type: 'bar',
                label: '2단계',
                data: [7, 4, 4, NaN, NaN],
                backgroundColor: 'rgba(255, 99, 132, 0.2)',
                borderColor: 'rgba(255,99,132,1)',
            },{
                type: 'bar',
                label: '3단계',
                data: [3, 3, 4, NaN, NaN],
                backgroundColor: 'rgba(255, 206, 86, 0.2)',
                borderColor: 'rgba(255, 206, 86, 1)',
            }]
        },
        options: {
            responsive: true,
            title: {
                display: false,
            },
            tooltips: {
                mode: 'index',
                intersect: true
            },
            scales: {
                yAxes: [{
                    stacked: true,
                    scaleLabel: {
                        display: false,
                    },
                }],
                xAxes: [{
                    stacked: true,
                    ticks: {
                        beginAtZero:true,
                    }
                }]
            },
            plugins: {
                datalabels: {
                    borderRadius: 4,
                    formatter: function(value, context) {
                        return value + '일';
                    },
                    font: {
                        weight: 'bold'
                    }
                }
            }
        }
    });
}
</script>
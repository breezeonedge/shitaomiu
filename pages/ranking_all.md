---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: page
title: 전체 랭킹
icon: fa fa-line-chart
permalink: ranking_all.html
cloudjs:
  - //cdn.jsdelivr.net/npm/chart.js@2.7.2/dist/Chart.bundle.min.js
  - //cdn.jsdelivr.net/npm/chartjs-plugin-datalabels@0.3.0
---

# 전체 랭킹

<canvas id="mnetChart" width="400" height="600"></canvas>

> 출처 : [엠넷 프로듀스48 랭킹](http://produce48.mnet.com/pc/rank/5)

---

<script>
window.onload = function() {

    var rank, ranks, r, count;
    var dataSet = {};
    var finalRanks = [];
    var rankInfos = JSON.parse('{{ site.data.rank | jsonify }}');
    var chartColors = {
        0: 'rgb(255, 99, 132)',
	    1: 'rgb(255, 159, 64)',
	    2: 'rgb(255, 205, 86)',
	    3: 'rgb(75, 192, 192)',
	    4: 'rgb(54, 162, 235)',
	    5: 'rgb(153, 102, 255)',
        6: 'rgb(201, 203, 207)'
    };

    for (rankNo in rankInfos) {

        if (rankInfos[rankNo].count == false)
            continue;

        ranks = rankInfos[rankNo].ranks;
        finalRanks = [];

        for (rankId in ranks) {

            rank = ranks[rankId];

            r = parseInt(rank.r);

            if (r < 22 && r >= 10) {
                finalRanks.push(rank.t);
            }
            count = parseInt(rank.c.replace(',',''));

            if (dataSet[rank.t] == undefined) {

                dataSet[rank.t] = {
                    type: 'bar',
                    backgroundColor: chartColors[r % 7],
                    label: rank.t,
                    rank: r,
                    data: []
                };
                dataSet[rank.t].data.push(count);
            } else {
                dataSet[rank.t].rank = r;
                count = count - dataSet[rank.t].data[0];
                dataSet[rank.t].data.push(count);
            };

        }

    };

    var datasets = [];

    for (dataNo in dataSet) {
        if (finalRanks.includes(dataNo)) {
            datasets.push(dataSet[dataNo]);
        }
    }

    datasets.sort(function(a, b){ return b.rank - a.rank});

    var mnetCtx = document.getElementById("mnetChart");
    var mnetChart = new Chart(mnetCtx, {
        type: 'bar',
        data: {
            labels: ["1차순위발표(12)", "2차순위발표(12)"],
            datasets: datasets
        },
        options: {
            responsive: true,
            title: {
                display: false,
            },
            legend: {
                display: false
            },
            scales: {
                yAxes: [{
                    stacked: true
                }],
                xAxes: [{
                    stacked: true
                }]
            },
            plugins: {
                datalabels: {
                    backgroundColor: function(context) {
                        return context.dataset.backgroundColor;
                    },
                    borderRadius: 4,
                    formatter: function(value, context) {
                        return context.dataset.label + ' : ' + value;
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
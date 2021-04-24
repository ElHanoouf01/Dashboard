# COVID-19 Dashboard
<!DOCTYPE html>
<html>
<head>
<script src="https://code.highcharts.com/maps/highmaps.js"></script>
<script src="https://code.highcharts.com/maps/modules/exporting.js"></script>
<script src="https://code.highcharts.com/mapdata/custom/world-palestine-highres.js"></script>
<script src="https://code.highcharts.com/maps/modules/data.js"></script>
</head>
<style>
  #container {
    height: 500px; 
    min-width: 310px; 
    max-width: 800px; 
    margin: 0 auto; 
  }
  .loading {
    margin-top: 10em;
    text-align: center;
    color: gray;
   }
</style>
<div id="container"></div>
<script>

var data = [
    ['gl', 0],
    ['sh', 1],
    ['bu', 2],
    ['lk', 3],
    ['as', 4],
    ['dk', 5],
    ['fo', 6],
    ['gu', 7],
    ['mp', 8],
    ['um', 9],
    ['us', 10],
    ['vi', 11],
    ['ca', 12],
    ['st', 13],
    ['jp', 14],
    ['cv', 15],
    ['dm', 16],
    ['sc', 17],
    ['nz', 18],
    ['ye', 19],
    ['jm', 20],
    ['ws', 21],
    ['om', 22],
    ['in', 23],
    ['vc', 24],
    ['bd', 25],
    ['sb', 26],
    ['lc', 27],
    ['fr', 28],
    ['nr', 29],
    ['no', 30],
    ['fm', 31],
    ['kn', 32],
    ['cn', 33],
    ['bh', 34],
    ['to', 35],
    ['fi', 36],
    ['id', 37],
    ['mu', 38],
    ['se', 39],
    ['tt', 40],
    ['sw', 41],
    ['br', 42],
    ['bs', 43],
    ['pw', 44],
    ['ec', 45],
    ['au', 46],
    ['tv', 47],
    ['mh', 48],
    ['cl', 49],
    ['ki', 50],
    ['ph', 51],
    ['gd', 52],
    ['ee', 53],
    ['ag', 54],
    ['es', 55],
    ['bb', 56],
    ['it', 57],
    ['mt', 58],
    ['mv', 59],
    ['sp', 60],
    ['pg', 61],
    ['vu', 62],
    ['sg', 63],
    ['gb', 64],
    ['cy', 65],
    ['gr', 66],
    ['km', 67],
    ['fj', 68],
    ['ru', 69],
    ['va', 70],
    ['sm', 71],
    ['am', 72],
    ['az', 73],
    ['ls', 74],
    ['tj', 75],
    ['ml', 76],
    ['dz', 77],
    ['tw', 78],
    ['uz', 79],
    ['tz', 80],
    ['ar', 81],
    ['sa', 82],
    ['nl', 83],
    ['ae', 84],
    ['ch', 85],
    ['pt', 86],
    ['my', 87],
    ['pa', 88],
    ['tr', 89],
    ['ir', 90],
    ['ht', 91],
    ['do', 92],
    ['gw', 93],
    ['hr', 94],
    ['th', 95],
    ['mx', 96],
    ['kw', 97],
    ['de', 98],
    ['gq', 99],
    ['cnm', 100],
    ['nc', 101],
    ['ie', 102],
    ['kz', 103],
    ['ge', 104],
    ['pl', 105],
    ['lt', 106],
    ['ug', 107],
    ['cd', 108],
    ['mk', 109],
    ['al', 110],
    ['ng', 111],
    ['cm', 112],
    ['bj', 113],
    ['tl', 114],
    ['tm', 115],
    ['kh', 116],
    ['pe', 117],
    ['mw', 118],
    ['mn', 119],
    ['ao', 120],
    ['mz', 121],
    ['za', 122],
    ['cr', 123],
    ['sv', 124],
    ['bz', 125],
    ['co', 126],
    ['kp', 127],
    ['kr', 128],
    ['gy', 129],
    ['hn', 130],
    ['ga', 131],
    ['ni', 132],
    ['et', 133],
    ['sd', 134],
    ['so', 135],
    ['gh', 136],
    ['ci', 137],
    ['si', 138],
    ['gt', 139],
    ['ba', 140],
    ['jo', 141],
    ['sy', 142],
    ['we', 143],
    ['il', 144],
    ['eg', 145],
    ['zm', 146],
    ['mc', 147],
    ['uy', 148],
    ['rw', 149],
    ['bo', 150],
    ['cg', 151],
    ['eh', 152],
    ['rs', 153],
    ['me', 154],
    ['tg', 155],
    ['mm', 156],
    ['la', 157],
    ['af', 158],
    ['jk', 159],
    ['pk', 160],
    ['bg', 161],
    ['ua', 162],
    ['ro', 163],
    ['qa', 164],
    ['li', 165],
    ['at', 166],
    ['sk', 167],
    ['sz', 168],
    ['hu', 169],
    ['ly', 170],
    ['ne', 171],
    ['lu', 172],
    ['ad', 173],
    ['lr', 174],
    ['sl', 175],
    ['bn', 176],
    ['mr', 177],
    ['be', 178],
    ['iq', 179],
    ['gm', 180],
    ['ma', 181],
    ['td', 182],
    ['kv', 183],
    ['lb', 184],
    ['sx', 185],
    ['dj', 186],
    ['er', 187],
    ['bi', 188],
    ['sn', 189],
    ['gn', 190],
    ['zw', 191],
    ['py', 192],
    ['by', 193],
    ['lv', 194],
    ['bt', 195],
    ['na', 196],
    ['bf', 197],
    ['ss', 198],
    ['cf', 199],
    ['md', 200],
    ['gz', 201],
    ['ke', 202],
    ['bw', 203],
    ['cz', 204],
    ['pr', 205],
    ['tn', 206],
    ['cu', 207],
    ['vn', 208],
    ['mg', 209],
    ['ve', 210],
    ['is', 211],
    ['np', 212],
    ['sr', 213],
    ['kg', 214]
];


// Prepare demo data
// Data is joined to map using value of 'hc-key' property by default.
// See API docs for 'joinBy' for more info on linking data and map.

// Create the chart
Highcharts.mapChart('container', {
    chart: {
        map: 'custom/world-palestine-highres'
    },

    title: {
        text: 'Covid 19 cases by country'
    },

    subtitle: {
//        text: 'Source map: <a href="http://code.highcharts.com/mapdata/custom/world-palestine-highres.js">Covid 19 Cases by country</a>'
    },

    mapNavigation: {
        enabled: true,
        buttonOptions: {
            verticalAlign: 'bottom'
        }
    },

    colorAxis: {
        min: 0
    },

    series: [{
        data: data,
        name: 'Random data',
        states: {
            hover: {
                color: '#BADA55'
            }
        },
        dataLabels: {
            enabled: true,
            format: '{point.name}'
        }
    }]
});



    </script>
</html>

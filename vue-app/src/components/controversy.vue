<template>
  <div>
    <div class="network"></div>
  </div>
</template>

<script>
import * as d3 from 'd3';

export default {
  name: "controversy",
  data() {
    return {
     dataset: {
      nodes: [
      { id: 1, name: 'Russia', img: 'img/russia.jpg', size: 500},
      { id: 2, name: 'Roman Abrahmovic', img: 'img/abrahmovic.png',size: 300},
      { id: 3, name: 'Alisha Usmanov', img: 'img/usmanov.png', size: 300 },
      { id: 4, name: 'Dmitry rybolovlev', img: 'img/ryoloblev.png', size: 300 },
      { id: 5, name: 'Suleyman Kerimov', img: 'img/kerimov.png', size: 300},
      { id: 6, name: 'Farhad Moshiri', img: 'img/moshiri.png', size: 150 },
      { id: 7, name: 'Gazprom', img: 'img/gazprom.jpg', size: 300 },
      { id: 8, name: 'Sibneft', img: 'img/sibneft.png', size: 100 },
      { id: 9, name: 'Aeroflot', img: 'img/aeroflot.png', size: 200 },
      { id: 10, name: 'Uralkali', img: 'img/uralkali.png', size: 200 },
      { id: 11, name: 'Megafon', img: 'img/megafon.jpg', size: 200 },
      { id: 12, name: 'MetalloInvest',img: 'img/metalloinvest.jpg',size: 100 },
      { id: 13, name: 'USM Holdings', img: 'img/usm.png', size: 200 },
      { id: 14, name: 'Chelsea', img: 'img/chelsea.png', size: 150 },
      { id: 15, name: 'Zenit St. Petersburg', img: 'img/zenit.png', size: 150},
      { id: 16, name: 'Monaco', img: 'img/monaco.jpg', size: 150 },
      { id: 17, name: 'Everton', img: 'img/everton.jpg', size: 125},
      { id: 18, name: 'Anzhi Makhachkala', img: 'img/anzhi.jpg', size: 150 },
      { id: 19, name: 'Manchester United', img: 'img/manu.jpg', size: 125 },
      { id: 20, name: 'Schalke', img: 'img/schalke.jpg', size: 125 },
      { id: 21, name: 'Red Star Belgrade', img: 'img/redstar.png', size: 125 },
      { id: 22, name: 'FIFA', img: 'img/fifa.png', size: 125 },
      { id: 23, name: 'UEFA', img: 'img/uefa.jpg', size: 125},
    ],
    links: [
      { source: 1, target: 2, color: "black"},
      { source: 1, target: 3 , color: "black"},
      { source: 1, target: 4 , color: "black"},
      { source: 1, target: 5 , color: "black"},
      { source: 1, target: 7 , color: "black"},
      { source: 1, target: 9, color: "black" },
      { source: 7, target: 2, color: "green" },
      { source: 7, target: 3 , color: "green"},
      { source: 7, target: 5 , color: "green"},
      { source: 8, target: 7, color: "red" },
      { source: 8, target: 2, color: "green" },
      { source: 15, target: 7, color: "red" },
      { source: 3, target: 6, color: "black" },
      { source: 11, target: 3, color: "red"},
      { source: 12, target: 3, color: "red"},
      { source: 13, target: 3, color: "red"},
      { source: 9, target: 2, color: "green" },
      { source: 14, target: 2, color: "red" },
      { source: 10, target: 4, color: "green" },
      { source: 10, target: 5, color: "green" },
      { source: 17, target: 6, color: "red" },
      { source: 17, target: 11, color: "blue"},
      { source: 17, target: 12, color: "blue" },
      { source: 11, target: 13, color: "green" },
      { source: 4, target: 16, color: "red" },
      { source: 5, target: 18, color: "red" },
      { source: 7, target: 19, color: "red" },
      { source: 7, target: 20, color: "red" },
      { source: 7, target: 21, color: "red" },
      { source: 7, target: 22, color: "red" },
      { source: 7, target: 23 , color: "red"},
      
    ],
  },
    simulation: null,
    svg: null,
    tooltip: null,
    };
  },
  
  methods: {
    initializeGraph() {
      const height = 1080;
      const width = 1920;
      const imgRadius = 10;
      const dim = 1000;
      const weightRadius = () => (imgRadius) / 3;

      const links = this.dataset.links;
      const nodes = this.dataset.nodes;

    this.tooltip = d3
      .select(".network")
      .append("div")
      .style("opacity", 0)
      .attr("class", "tooltip")
      .style("background-color", "black")
      .style("border", "solid")
      .style("border-width", "2px")
      .style("border-radius", "5px");

    const mouseover = () => {
        this.tooltip.style('opacity', 1);
        d3.select(this).style('stroke', 'black').style('opacity', 1);
      };

     const mousemove = (event, d) => {
        this.tooltip
          .html("The exact value of<br>this cell is: " + d.name)
          .style('left', d3.pointer(event, this)[0] + 70 + 'px')
          .style('top', d3.pointer(event, this)[1] + 'px');
      };

    const mouseleave = () => {
        this.tooltip.style('opacity', 0);
        d3.select(this).style('stroke', 'none').style('opacity', 0.8);
    };
    this.simulation = d3
        .forceSimulation(nodes)
        .force('link', d3.forceLink(links).id((d) => d.id))
        .force('charge', d3.forceManyBody().strength())
        .force('center', d3.forceCenter(dim / 2, dim / 2))
        .force('collide', d3.forceCollide().radius(30));
      
      this.svg = d3
        .select(".network")
        .append('svg')
        .attr('width', width)
        .attr('height', height)
        .attr('viewbox', [0, 0, dim, dim]);

      this.svg
        .append('defs')
        .append('clipPath')
        .attr('id', 'clip-circle')
        .append('circle')
        .attr('cx', imgRadius)
        .attr('cy', imgRadius)
        .attr('r', imgRadius);

      //  const link = this.svg
      //   .append('g')
      //   .attr('stroke', '#999')
      //   .attr('stroke-opacity', 5)
      //   .selectAll('line')
      //   .data(links)
      //   .join('line')
      //   .attr('stroke-width', 2)
      //   .attr('stroke', (d) => d.color);

      const node = this.svg
        .append('g')
        .attr('stroke', 'orange')
        .attr('stroke-width', 1.5)
        .selectAll('g')
        .data(nodes)
        .join('g');

      node.append('circle').attr('r', weightRadius).attr('fill', 'black');
      
    node
      .append('defs')
      .append('clipPath')
      .attr('id', (d) => 'clip-' + d.id)
      .append('circle')
      .attr('cx', weightRadius)
      .attr('cy', weightRadius)
      .attr('r', weightRadius);

    node.append('title').text((d) => d.name);

    node
     .append('g')
     .attr('clip-path', (d) => `url(#clip-${d.id})`)
     .attr('transform', (d) => {
          const offset = (d.size / 5 + imgRadius) / 2;
          return `translate(${-offset}, ${-offset})`;
        })
        .append('image')
        .attr('xlink:href', (d) => d.img)
        .attr('width', (d) => d.size / 5 + imgRadius)
        .on('mouseover', mouseover)
        .on('mousemove', mousemove)
        .on('mouseleave', mouseleave);

      this.simulation.on('tick', this.ticked);
    },
    ticked() {
      const link = this.svg.select('g').selectAll('line');
      const node = this.svg.select('g').selectAll('g');

      link
        .attr('x1', (d) => d.source.x)
        .attr('y1', (d) => d.source.y)
        .attr('x2', (d) => d.target.x)
        .attr('y2', (d) => d.target.y);

      node.attr('transform', (d) => `translate(${d.x},${d.y})`);
    },
    
   },
  mounted(){
    this.initializeGraph();
  },
};
</script>

<style>
.network {
  width: 100vw;
  height: 100vh;
  background-color: white;
}
</style>

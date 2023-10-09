---
tags: 游戏 王者荣耀
aliases: 守约, 百里
---
![[百里守约绝影神枪.png]]

> Give me a target, and I'll return silence to you. — Bai Li Shou Yue

# 人物简介

````ad-flex

<div>

<br>

职业：射手
派系：长城守卫军
标签：输出
特性：超远攻击

</div>



<div>

```dataviewjs
const chartData = {
  type: 'radar',
  data: {
    labels: ['生命', '攻击', '射程', '防御', '移速', '暴击'],
    datasets: [{
      label: '王者英雄六维',
      data: [2,5,5,2,4,0],
      backgroundColor: [
        'rgba(255, 99, 132, 0.2)'
      ],
      borderColor: [
        'rgba(255, 99, 132, 1)'
      ],
      borderWidth: 1
    }]
  },
	options: {
    fill: true,
		scales: {
			r: {
				min: 0,
				max: 5,
				ticks: { display: false }
			},
		},
    plugins: {
		  legend: {
		    display: false
		  },
		}
	},
};

const c = this.container.createEl('div');
c.style.width = '60%';
window.renderChart(chartData, c);
```

</div>

````
## Abilities

| Ability            | Cooldown | <span style='white-space: nowrap'>Cost</span> | Description                                                                                                                                                                                                                                                                                                                                   |
| ------------------ | -------- | ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span style='white-space: nowrap'>Aim</span> | 0        | 0                                         | Passive: Bai Li Shou Yue's basic attacks deal 190% physical bonus physical damage but have a longer attack interval and cannot critically strike; Bai Li Shou Yue converts 1% of his critical strike chance into 2.5 points of physical attack power; Out of combat, Bai Li Shou Yue can hide at the edge of terrain, enter stealth mode, and increase his movement speed by 16% to 30%, with movement speed growing with his level. |
| <span style='white-space: nowrap'>Quiet Eye</span> | 1.5      | 30                                        | Bai Li Shou Yue places a vision device under his feet, gaining full vision within a range of 600 to 1000, growing with the skill level; The vision device can be prepared every 50/48/46/44/42/40 seconds, with a maximum of 3 stored; At most 3 vision devices can be placed, each lasting 300 seconds; When the enemy hero occupies the vision device, it becomes invalid; Passive: When Bai Li Shou Yue remains still, he gains 1 layer of ambush effect per second, with each layer of ambush effect increasing his physical penetration by 7/8/9/10/11/12%, stacking up to 5 layers; Ambush effect disappears after moving. |
| <span style='white-space: nowrap'>Furious Winds</span> | 1.5      | 60                                        | Bai Li Shou Yue starts aiming and attempts to perform a sniper shot, dealing 600/720/840/960/1080/1200 (+250% bonus physical damage) physical damage to the hit target and reducing their movement speed by 90% for 0.5 seconds; Aiming takes 2 seconds, but bullets may deviate when aiming is incomplete; Up to 3 bullets can be stored for this skill (affected by cooldown reduction). |
| <span style='white-space: nowrap'>Escape</span>       | <span style='white-space: nowrap'>25/20/15</span> | <span style='white-space: nowrap'>100</span> | Bai Li Shou Yue jumps backward and shoots in a specified direction, dealing 500/700/900 (+168% physical bonus) physical damage and reducing the target's movement speed by 50% for 2 seconds; After landing, Bai Li Shou Yue increases his movement speed by 30% for 2 seconds, but normal attacks or skill attacks will immediately stop increasing movement speed. |

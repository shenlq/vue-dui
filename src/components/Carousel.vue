<template>
	<div :class="['carousel', options.length>0?'':'carousel-empty']">
		<ol class="carousel-indicators" v-if="options.length > 1">
			<li :class="{'active': index == activeIndex}" v-for="(index, item) in options"></li>
		</ol>
		<div @touchstart="touchstart" @touchend="touchend"
			:class="['carousel-item',
			index==activeIndex?'active':'',
			(index - activeIndex + options.length)%options.length == 1?'next':'',
			(index - activeIndex + options.length)%options.length == 2?'prev':'',
			action=='next' && index==activeIndex?'left':'',
			action=='prev' && index==activeIndex?'right':'',
			action=='next' && (index - activeIndex + options.length)%options.length == 1?'left':'',
			action=='prev' && (index - activeIndex + options.length)%options.length == 2?'right':''
			]" v-for="(index, item) in options">
			<a v-if="item.href" :href="item.href" target="_blank">
				<img class='carousel-img' :src="item.image"/>
			</a>
			<a v-if="item.vLink" v-link='item.vLink'>
				<img class='carousel-img' :src="item.image"/>
			</a>
			<img v-if="!item.href && !item.vLink" class='carousel-img' :src="item.image"/>
		</div>
	</div>
</template>

<script>
	export default {
		props: {
			interval: {
				type: Number,
				default: 3000
			},
			options: {
				type: Array,
				coerce(val){
					if(!val || val.length < 1){
						return [];
					}

					return val.map((item, index) => {
						if("[object Object]" == Object.prototype.toString.call(item)){
							return item;
						}else{
							return {image: item};
						};
					});
				}
			},
			debounce: {
				default: 600
			}
		},
		data(){
			return {
				activeIndex: 0,
				action: 'none'
			};
		},
		created(){
		},
		destroyed(){
			clearInterval(this.intervalCarousel);
		},
		watch: {
			options(){
				this.options.length > 0 && this.addInterval();
			}
		},
		methods: {
			//下一个
			next(){
				this.action = 'next';
				setTimeout(() => {
					this.activeIndex = (this.activeIndex + 1) % this.options.length;
					this.action = 'none';
				}, this.debounce);
			},
			//前一个
			prev(){
				this.action = 'prev';
				setTimeout(() => {
					this.activeIndex = (this.activeIndex - 1 + this.options.length) % this.options.length;
					this.action = 'none';
				}, this.debounce);
			},
			addInterval(){
				this.options.length > 1 && (this.intervalCarousel = setInterval(() => {
					this.next();
				}, this.interval));
			},
			touchstart(event){
//				event.preventDefault();
				this._touchStartX = event.targetTouches[0].pageX;
				this.intervalCarousel && clearInterval(this.intervalCarousel);
			},
			touchend(event){
//				event.preventDefault();
				let touchStartX = event.changedTouches[0].pageX;
				if(touchStartX > this._touchStartX + 10){
					this.prev();
				}else if(touchStartX < this._touchStartX - 10){
					this.next();
				}
				this.addInterval();
			}
		}
	};
</script>
<template>
	<page backgroundSpanUnderStatusBar="true">

    <ActionBar>
        <StackLayout orientation="horizontal" height="80">
          <Label text="HOME" fontSize="24" color="black" verticalAlignment="center"/>
        </StackLayout>
      </ActionBar>

		<GridLayout rows="auto,auto,*,auto" columns="auto">
			<GridLayout v-show="selectedTabview == 0" row="2" width="100%" backgroundColor="white">
				<ListView ref="listview" separatorColor="transparent" for="item in items" :key="index">
					<v-template>
						<item :item="item" @clicked="showItem(item)" />
					</v-template>
				</ListView>
			</GridLayout>

			<GridLayout v-show="selectedTabview == 1" row="2" width="100%" backgroundColor="white">		
				<ListView ref="listview" separatorColor="transparent" for="item in itemsCategory" :key="index">
					<v-template>
						<Category :item="item"> </Category>
					</v-template>
				</ListView>
			</GridLayout>

			<GridLayout v-show="selectedTabview == 2" row="2" width="100%" backgroundColor="white">		
			</GridLayout>

			<navBottom row="4" />

		</GridLayout>
</page>
</template>
<script>
	import { isIOS, isAndroid } from 'tns-core-modules/platform'
	import navBottom from "./custom/navBottom";
	import Item from "./custom/item";
	import Category from "./custom/category";
	import ItemDetails from "./ItemDetails";

	const gestures = require("ui/gestures"); 
	const app = require("application");

export default {
	components: {
		navBottom,
		Item,
		Category
	},
	computed: {
		itemsCategory(){
			return this.category.slice().reverse();
		}
  },
  
	data() {
		return {
			lastDelY: 0,
			headerCollapsed: false,
			selectedTab: 0,
			selectedTabview: 0,
			items: [{
				name: "Add Flight",
				cover: "~/assets/images/1.jpg",
				images: [
						{src: "~/assets/images/food/burger/burger1.jpg"},
						{src: "~/assets/images/food/burger/burger2.jpg"},
						{src: "~/assets/images/food/burger/burger3.jpg"},
						{src: "~/assets/images/food/burger/burger4.jpg"},
						{src: "~/assets/images/food/burger/burger5.jpg"},
						{src: "~/assets/images/food/burger/burger6.jpg"}
					],
				category: "Enter Flight Details",
			},
			{
				name: "Flight check in",
				cover: "~/assets/images/2.jpg",
				images: [
					{src: "~/assets/images/food/pancake/pancake1.jpg"},
					{src: "~/assets/images/food/pancake/pancake2.jpg"},
					{src: "~/assets/images/food/pancake/pancake3.jpg"},
					{src: "~/assets/images/food/pancake/pancake4.jpg"},
					{src: "~/assets/images/food/pancake/pancake5.jpg"},
					{src: "~/assets/images/food/pancake/pancake6.jpg"}
				],
				category: "Flight Check-in",
			},
			],
			category: [
			{
				cover: "~/assets/images/food/burger640.jpg",
				category: "BURGER",
				count: "13",
			},
			{
				cover: "~/assets/images/food/pancake640.jpg",
				category: "PANCAKE",
				count: "5",
			},
			{
				cover: "~/assets/images/food/cake640.jpg",
				category: "CAKE",
				count: "9",
			},
			{
				cover: "~/assets/images/food/beer640.jpg",
				category: "BEER",
				count: "7",
			},
		
			]
		};
	},
	methods: {
		search(){
			console.log('search')
		},
		bell(){
			console.log('bell')
		},
		showItem(payload) {
			this.$navigateTo(ItemDetails,{
				props: {
					item: payload
				},
				animated: true,
				transition: {
					name: "slideTop",
					duration: 380,
					curve: "easeIn"
				}
			})
		},
		
		popular() {
			this.selectedTabview = 0;
		},
		showCategory() {
			this.selectedTabview = 1;
		},
		showPromos() {
			this.selectedTabview = 2;
		},
		left() {
			this.selectedTab = 0;
		},
		right() {
			this.selectedTab = 1;
		},
		home() {
			this.selectedTab = 2;
		},
		logout() {
			this.selectedTab = 3;
		}
	}
};
</script>

<style>

ActionBar {
        background-color: #FFC10D;
        color: #ffffff;
        
    }

.tabview.active {
	border-bottom-color: white;
	border-bottom-width: 3;
	margin: 0;
	height: 50;
}
.tabviewText {
	margin-top: 15;
	margin-bottom: 5;
	font-size: 13;
	color: #d8d2d2;
	horizontal-align: center;
}
.tabviewText.active {
	margin-top: 0;
	margin-bottom: 5;
	font-weight: bold;
	color: white;
	vertical-align: center;
}
.navTab {
	background-color: #bd2122;
}
.navTabview {
	background-color: blue;
}
.status-img {
	margin-top: 4;
	margin-right: 20;
	width: 30;
	height: 30;
}
.status-profile {
	border-width: 1;
	border-color: #ffffff;
	background-color: #f1ebeb;
	border-radius: 50%;
	margin-top: 4;
	margin-right: 15;
	width: 30;
	height: 30;
}
.status-title {
	color: white;
	font-size: 18;
	margin-left: 15;
	margin-top: 8;
	horizontal-align: left;
	vertical-align: center;
}
</style>
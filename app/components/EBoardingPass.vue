<template>
    <Page class="backgroundColor">

		<ActionBar>
        <StackLayout orientation="horizontal" height="80">
          <Label text="E-BOARDING PASS" fontSize="24" color="black" verticalAlignment="center"/>
        </StackLayout>
      </ActionBar>
<ScrollView ref="scrollView" @scroll="onScroll">
      <AbsoluteLayout>
        <Image top="40" left="25" src="~/images/eBoardingPassCard.png"/>
        <Button top="765" class="continue_button" text="CONTINUE" @tap="continueButton"/>
<navBottom top="810" row="4" />
      </AbsoluteLayout>
      </ScrollView>
    </Page>
</template>

<script >
import navBottom from "./custom/navBottom";
import AddFlight from "./AddFlight";
import SecurityPolicy from "./SecurityPolicy";

  export default {
	  components: {
		navBottom
	},
    data() {
      return {
    }
  },
  methods: {
    continueButton() {
       this.$navigateTo(SecurityPolicy);
    }
  }
};
</script>

<style scoped>
ActionBar {
    background-color: #FFC10D;
    color: #ffffff;  
}

.backgroundColor {
	background-color: #EAEAEA;
    height: 100%;
    width: 100%;
}
.cardTextColor {
	color: #2699FB;
}
.textfld{
    width: 320;
    border-color: #BCE0FD;
    color: black;
    text-align: center;
    background-color: white;
    font-size: 12;
}

.continue_button{
    background-color: #2699FB;
    border-radius: 3;
    color: white;
    font-family: Arial, Helvetica, sans-serif;
    font-size: 11;
    height: 48;
    width: 100%;
    font-weight: bold;
}

</style>

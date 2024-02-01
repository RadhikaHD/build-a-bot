<template>
    <div>
        <div class="top-row">
          <div class="top part">
            <img v-bind:src="availableParts.heads[selectedHeadIndex].src" title="head"/>
            <button v-on:click="selectPreviousHead()" class="prev-selector">&#9668;</button>
            <button v-on:click="selectNextHead()" class="next-selector">&#9658;</button>
          </div>
        </div>
        <div class="middle-row">
          <div class="left part">
            <img v-bind:src="availableParts.arms[selectedLeftArmIndex].src" title="left arm"/>
            <button v-on:click="selectPreviousLeftArm()" class="prev-selector">&#9650;</button>
            <button v-on:click="selectNextLeftArm()" class="next-selector">&#9660;</button>
          </div>
          <div class="center part">
            <img v-bind:src="availableParts.torsos[selectedTorsoIndex].src" title="torso"/>
            <button v-on:click="selectPreviousTorso()" class="prev-selector">&#9668;</button>
            <button v-on:click="selectNextTorso()" class="next-selector">&#9658;</button>
          </div>
          <div class="right part">
            <img v-bind:src="availableParts.arms[selectedRightArmIndex].src" title="right arm"/>
            <button v-on:click="selectPreviousRightArm()" class="prev-selector">&#9650;</button>
            <button v-on:click="selectNextRightArm()" class="next-selector">&#9660;</button>
          </div>
        </div>
        <div class="bottom-row">
          <div class="bottom part">
            <img v-bind:src="availableParts.bases[selectedBaseIndex].src" title="base"/>
            <button v-on:click="selectPreviousBase()" class="prev-selector">&#9668;</button>
            <button v-on:click="selectNextBase()" class="next-selector">&#9658;</button>
          </div>
        </div>
      </div>
</template>

<script>
import availableParts from '../data/parts';

function getPreviousValidIndex(index, length) {
  const deprecatedIndex = index - 1;
  return deprecatedIndex < 0 ? length - 1 : deprecatedIndex;
}

function getNextValidIndex(index, length) {
  const incrementedIndex = index + 1;
  return incrementedIndex > length - 1 ? 0 : incrementedIndex;
}

export default {
  name: 'robotbuilder',
  data() {
    return {
      availableParts,
      selectedHeadIndex: 0,
      selectedLeftArmIndex: 0,
      selectedRightArmIndex: 0,
      selectedTorsoIndex: 0,
      selectedBaseIndex: 0,
    };
  },
  methods: {
    selectNextHead() {
      this.selectedHeadIndex = getNextValidIndex(this.selectedHeadIndex,
        this.availableParts.heads.length);
    },
    selectPreviousHead() {
      this.selectedHeadIndex = getPreviousValidIndex(this.selectedHeadIndex,
        this.availableParts.heads.length);
    },
    selectNextLeftArm() {
      this.selectedLeftArmIndex = getNextValidIndex(this.selectedHeadIndex,
        this.availableParts.heads.length);
    },
    selectPreviousLeftArm() {
      this.selectedLeftArmIndex = getPreviousValidIndex(this.selectedHeadIndex,
        this.availableParts.heads.length);
    },
    selectNextTorso() {
      this.selectedTorsoIndex = getNextValidIndex(this.selectedHeadIndex,
        this.availableParts.heads.length);
    },
    selectPreviousTorso() {
      this.selectedTorsoIndex = getPreviousValidIndex(this.selectedHeadIndex,
        this.availableParts.heads.length);
    },
    selectNextRightArm() {
      this.selectedRightArmIndex = getNextValidIndex(this.selectedHeadIndex,
        this.availableParts.heads.length);
    },
    selectPreviousRightArm() {
      this.selectedRightArmIndex = getPreviousValidIndex(this.selectedHeadIndex,
        this.availableParts.heads.length);
    },
    selectNextBase() {
      this.selectedBaseIndex = getNextValidIndex(this.selectedHeadIndex,
        this.availableParts.heads.length);
    },
    selectPreviousBase() {
      this.selectedBaseIndex = getPreviousValidIndex(this.selectedHeadIndex,
        this.availableParts.heads.length);
    },
  },
};
</script>

<style>
.part {
    position: relative;
    width:165px;
    height:165px;
    border: 3px solid #aaa;
  }
  .part img {
    width:165px;
  }
  .top-row {
    display:flex;
    justify-content: space-around;
  }
  .middle-row {
    display:flex;
    justify-content: center;
  }
  .bottom-row {
    display:flex;
    justify-content: space-around;
    border-top: none;
  }
  .head {
    border-bottom: none;
  }
  .left {
    border-right: none;
  }
  .right {
    border-left: none;
  }
  .left img {
    transform: rotate(-90deg);
  }
  .right img {
    transform: rotate(90deg);
  }
  .bottom {
    border-top: none;
  }
  .prev-selector {
    position: absolute;
    z-index:1;
    top: -3px;
    left: -28px;
    width: 25px;
    height: 171px;
  }
  .next-selector {
    position: absolute;
    z-index:1;
    top: -3px;
    right: -28px;
    width: 25px;
    height: 171px;
  }
  .center .prev-selector, .center .next-selector {
    opacity:0.8;
  }
  .left .prev-selector {
    top: -28px;
    left: -3px;
    width: 144px;
    height: 25px;
  }
  .left .next-selector {
    top: auto;
    bottom: -28px;
    left: -3px;
    width: 144px;
    height: 25px;
  }
  .right .prev-selector {
    top: -28px;
    left: 24px;
    width: 144px;
    height: 25px;
  }
  .right .next-selector {
    top: auto;
    bottom: -28px;
    left: 24px;
    width: 144px;
    height: 25px;
  }
  .right .next-selector {
    right: -3px;
  }
</style>

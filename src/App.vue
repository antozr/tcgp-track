<script setup>
import HelloWorld from './components/HelloWorld.vue'
import './assets/js/promo-stats.js';
import { onMounted, onUnmounted, ref } from 'vue';
import DataPromo from './assets/json/Promo-A-tcg.json';

/// ref for categorie to tab
const checked = ref([]);
const TrueCard = ref(0);
const ShopCard = ref(0);
const MissionCard = ref(0);
const PromoCard = ref(0);
const WonderCard = ref(0);
/// ref count nb categories
const nbPromoCard = ref(0);
const nbShopCard = ref(0);
const nbMissionCard = ref(0);
const nbWonderCard = ref(0);
/// ref percent card 
const percentMissAll = ref(100);
const percentMissShop = ref(100);
const percentMissWonder = ref(100);
const percentMissMission = ref(100);
const percentMissPromo = ref(100);

const percentWinAll = ref(0);
const percentWinShop = ref(0);
const percentWinWonder = ref(0);
const percentWinMission = ref(0);
const percentWinPromo = ref(0);

const labels = [
  { text: 'Check', field: "check" },
  { text: 'Card_ID', field: "id" },
  { text: 'Card_Name', field: "name" },
  { text: 'Pack', field: "pack" },
  { text: 'Number_card', field: "card- ID" },
];

const labelsResult = [
  { text: " / ", field: "rowName" },
  { text: "% Owned", field: "owned" },
  { text: "% missing", field: "missing" },
  { text: "Fraction", field: "fraction" }
];
const dataResult = [
  {
    id: 0, rowName: "Total", owned: percentWinAll.value + '%', missing: percentMissAll.value + '%', fraction: ' / ' + DataPromo.length
  },
  {
    id: 1, rowName: "Shop", owned: percentWinShop.value + '%', missing: percentMissShop.value + '%', fraction: ' /' + nbShopCard.value
  },
  {
    id: 2, rowName: "Mission", owned: percentWinMission.value + '%', missing: percentMissMission.value + '%', fraction: '/'
  },
  {
    id: 3, rowName: "Promo pack", owned: percentWinPromo.value + '%', missing: percentMissPromo.value + '%', fraction: '/'
  },
  {
    id: 4, rowName: "Wonder pick", owned: percentWinWonder.value + '%', missing: percentMissWonder.value + '%', fraction: '/'
  }
]
const data = [
  { id: 1, name: 'Foo', numbers: 0, pack: "shop" },
  { id: 2, name: 'Bar', numbers: 0, pack: "mission" }
];



if (checked.value.length > 0) {
  console.log(checked.value);
  numbCard = data.length;

  console.log(numbCard);

}


/////

onMounted(() => {

  console.log('heueueu')
  let missionNb = 0;
  let shopNb = 0;
  let promoNb = 0;
  let wonderNb = 0;
  for (let index = 0; index < 25; index++) {

    console.log(DataPromo[index].pack);


    if (DataPromo[index].pack.includes('Shop')) {
      let oldShop = shopNb;
      shopNb = oldShop + 1;
      //console.log(shopNb);
      nbShopCard.value = shopNb;


    } else if (DataPromo[index].pack.includes('Mission')) {

      missionNb = missionNb + 1;
      nbMissionCard.value = missionNb;
    } else if (DataPromo[index].pack.includes('Promo')) {
      promoNb = promoNb + 1;
      nbPromoCard.value = promoNb;

    } else if (DataPromo[index].pack.includes('Wonder')) {
      wonderNb = wonderNb + 1;
      nbWonderCard.value = wonderNb;
    }

    if (index == 24) {
      nbMissionCard.value = missionNb;
      nbPromoCard.value = promoNb;
      nbShopCard.value = shopNb;
      nbWonderCard.value = wonderNb;
      //console.log(nbMissionCard.value + '---');
      //console.log(missionNb + '---');

    }

  }
  console.log('fini');

})


/////


function hoverViewCatLine(event) {
  console.log(event.target.id);

  let allROwLigne = document.querySelectorAll('.tab__row--item');
 // console.log(allROwLigne[0].ariaLabel);
  const newShopAll = [];
  var chnageColor = false;
  var nameCat = 'rien';
  //console.log(allROwLigne);

  allROwLigne.forEach(el => {
    el.classList.add('tab__row--opa');
  });

  //
  if (event.target.id == "Shop") {
    for (let index = 0; index < allROwLigne.length; index++) {

      if (allROwLigne[index].ariaLabel == "Shop") {
        newShopAll.push(allROwLigne[index]);
        nameCat = 'Shop';
        console.log(newShopAll);

      }
      if (index === allROwLigne.length - 1) {
        chnageColor = true;
      }
    }
    if (chnageColor === true) {
      newShopAll.forEach(el => (
        console.log(el),
        el.classList.add('tab__row--shop')

      ))
    }

  } 
  if (event.target.id == "Mission") {

    
    for (let index = 0; index < allROwLigne.length; index++) {

      if (allROwLigne[index].ariaLabel == "Mission") {
        newShopAll.push(allROwLigne[index]);
        nameCat = 'Shop';
        console.log(newShopAll);

      }
      if (index === allROwLigne.length - 1) {
        chnageColor = true;
      }
    }
    if (chnageColor === true) {
      newShopAll.forEach(el => (
        console.log(el),
        el.classList.add('tab__row--mission')

      ))
    }

  } 
  if (event.target.id == "Promo pack") {

    
    for (let index = 0; index < allROwLigne.length; index++) {

      if (allROwLigne[index].ariaLabel == "Promo pack") {
        newShopAll.push(allROwLigne[index]);
        nameCat = 'Shop';
        console.log(newShopAll);

      }
      if (index === allROwLigne.length - 1) {
        chnageColor = true;
      }
    }
    if (chnageColor === true) {
      newShopAll.forEach(el => (
        console.log(el),
        el.classList.add('tab__row--mission')

      ))
    }

  } 
  if (event.target.id == "Wonder pick") {

    
    for (let index = 0; index < allROwLigne.length; index++) {

      if (allROwLigne[index].ariaLabel == "Wonder pick") {
        newShopAll.push(allROwLigne[index]);
        nameCat = 'Shop';
        console.log(newShopAll);

      }
      if (index === allROwLigne.length - 1) {
        chnageColor = true;
      }
    }
    if (chnageColor === true) {
      newShopAll.forEach(el => (
        console.log(el),
        el.classList.add('tab__row--mission')

      ))
    }

  } 
}

function underHoverCatLine(event) {
  let allROwLigne = document.querySelectorAll('.tab__row--item');
  allROwLigne.forEach(el => {
    el.classList.remove('tab__row--opa');
    el.classList.remove('tab__row--shop');
    el.classList.remove('tab__row--mission');
  })
}
/////

function verifyPercentCat(event, refBalise, refBaliseMin, refTargetName, nbCard) {

  /// check si true => augmente pourcentage sinon diminue + calcule % sur total 
  ///

  if (event.target.checked === true) {
    if (event.target.value.includes(refTargetName)) {
      let oldMissPercent = refBaliseMin.value;
      let oldWinPercent = refBalise.value;
      let gainClick = (100 / nbCard.value);
      //console.log(gainClick);
      //console.log(nbCard.value);
      if (oldMissPercent <= 0) {
        refBaliseMin.value = 0;
      } else {
        refBaliseMin.value = oldMissPercent - gainClick;
      }
      if (oldWinPercent >= 100) {
        refBalise.value = 100;
      } else {
        refBalise.value = oldWinPercent + gainClick;
      }

    }
    else if (refTargetName === "all") {

      let oldMissPerc = percentMissAll.value;
      let oldWinPerc = percentWinAll.value;
      let gainClick = (100 / DataPromo.length);

      if (oldMissPerc <= 0) {
        percentMissAll.value = 0;
      } else {
        percentMissAll.value = oldMissPerc - gainClick;
      }
      if (oldWinPerc >= 100) {
        percentWinAll.value = 100;
      } else {
        percentWinAll.value = gainClick + oldWinPerc;
      }
    }
  }
}


/////
function verifyIncludeNameCat(event, refBalise, refTargetName) {
  // console.log(event + "----" + refTargetName);

  if (event.target.checked === true) {
    if (event.target.value.includes(refTargetName)) {
      let oldShopCard = refBalise.value;
      refBalise.value = oldShopCard + 1;
      console.log(refBalise.value);

    }

  } else {
    if (refBalise.value > 0) {
      let oldShopCard = refBalise.value;
      refBalise.value = oldShopCard - 1;
    } else {
      refBalise.value = 0;
    }
  }
}

/////
function UpdateTrueCard(event) {

  console.log(event.target.checked)
  console.log(event.target.value)
  console.log(event);

  verifyIncludeNameCat(event, MissionCard, "Mission");
  verifyIncludeNameCat(event, ShopCard, "Shop");
  verifyIncludeNameCat(event, PromoCard, "Promo");
  verifyIncludeNameCat(event, WonderCard, "Wonder");

  verifyPercentCat(event, percentWinMission, percentMissMission, "Mission", nbMissionCard);
  verifyPercentCat(event, percentWinShop, percentMissShop, "Shop", nbShopCard);
  verifyPercentCat(event, percentWinPromo, percentMissPromo, "Promo", nbPromoCard);
  verifyPercentCat(event, percentWinWonder, percentMissWonder, "Wonder", nbWonderCard);
  verifyPercentCat(event, percentWinAll, percentMissAll, "all", DataPromo.length);
  if (event.target.checked === true) {
    let oldTrueCard = TrueCard.value;
    TrueCard.value = oldTrueCard + 1;


  } else {

    if (TrueCard.value > 0) {
      let oldTrueCard = TrueCard.value;
      TrueCard.value = oldTrueCard - 1;
    }

  }



}
</script>

<template>
  <div class="sect sect--row">


    <div class="sect__tab">

      <table class="tab">
        <thead>
          <tr>
            <td v-for="(label, labelIndex) in labels" :key="labelIndex">
              {{ label.text }}
            </td>
          </tr>
        </thead>

        <tbody>
          <tr v-for="(item, itemIndex) in DataPromo" :key="itemIndex" class="tab__row--item" :aria-label="item.pack">

            <td v-for="(label, labelIndex) in labels" :key="labelIndex">

              {{ item[label.field] }}
              <div v-show="labelIndex === 0">

                <input type="checkbox" :id="item.id" :value="item.pack + item.id" :key="item.id"
                  @click='UpdateTrueCard' />
              </div>
            </td>
          </tr>
        </tbody>
      </table>
    </div>

    <div class="sect__result">
      <table>
        <thead>
          <tr>
            <td v-for="(label, labelIndex) in labelsResult" :key="labelIndex">
              {{ label.text }}
            </td>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, itemIndex) in dataResult" :key="itemIndex" @mouseenter="hoverViewCatLine"
            @mouseleave="underHoverCatLine" :id="item.rowName">

            <td v-for="(label, labelIndex) in labelsResult" :key="labelIndex">

              <span v-show="labelIndex === 0">
                {{ item[label.field] }}
              </span>

              <span v-show="labelIndex === 1">
                <span v-show="item.id == 1">
                  {{ percentWinShop }}
                </span>
                <span v-show="item.id == 2">
                  {{ percentWinMission }}
                </span>
                <span v-show="item.id == 3">
                  {{ percentWinPromo }}
                </span>
                <span v-show="item.id == 4">
                  {{ percentWinWonder }}
                </span>
                <span v-show="item.id == 0">
                  {{ percentWinAll.toFixed(1) }}
                </span>
                %
              </span>
              <span v-show="labelIndex === 2">
                <span v-show="item.id == 1">
                  {{ percentMissShop }}
                </span>
                <span v-show="item.id == 2">
                  {{ percentMissMission }}
                </span>
                <span v-show="item.id == 3">
                  {{ percentMissPromo }}
                </span>
                <span v-show="item.id == 4">
                  {{ percentMissWonder }}
                </span>
                <span v-show="item.id == 0">
                  {{ percentMissAll.toFixed(1) }}
                </span>
                %
              </span>


              <span v-show="labelIndex === 3">
                <span v-show="item.id == 1">
                  {{ ShopCard }} / {{ nbShopCard }}
                </span>
                <span v-show="item.id == 2">
                  {{ MissionCard }} / {{ nbMissionCard }}
                </span>
                <span v-show="item.id == 3">
                  {{ PromoCard }} / {{ nbPromoCard }}
                </span>
                <span v-show="item.id == 4">
                  {{ WonderCard }} / {{ nbWonderCard }}
                </span>
                <span v-show="item.id == 0">
                  {{ TrueCard }} / {{ DataPromo.length }}
                </span>

              </span>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>

  <!--<HelloWorld msg="Vite + Vue" />-->
</template>

<style lang="scss" scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}

.sect {
  position: relative;

  &--row {
    display: flex;
    flex-direction: row;
  }

  &__result {
    position: sticky;
    top: 20px;
    height: 50vh;
  }
}

.tab {
  &__row {
    transition: 0.6s ease-in;

    &--opa {
      opacity: 0.6;
      transition: 0.6s ease-out;
    }

    &--shop {
      transition: 0.6s ease-out;
      background: rgb(142, 187, 255);
      color: #1d1d1d;
      opacity: 1;
    }

    &--mission {
      transition: 0.6s ease-out;
      background: rgb(250, 240, 155);
      color: #1d1d1d;
      opacity: 1;
    }
  }
}
</style>

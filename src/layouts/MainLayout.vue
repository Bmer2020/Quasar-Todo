<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-img
        src="/statics/mountain.jpg"
        class="header-image absolute-top"
      />

      <div class="q-header-content"> 
        <q-toolbar>
          <q-btn
            flat
            dense
            round
            icon="menu"
            aria-label="Menu"
            @click="toggleLeftDrawer"
          />

          <q-toolbar-title>
            Quasar App
          </q-toolbar-title>

          <div>Quasar v{{ $q.version }}</div>
        </q-toolbar>

        <div class="q-px-lg q-pt-xl q-mb-md text-white"> 
          <div class="text-h3">Todo</div>
          <div class="text-subtitle1">{{todaysDate }}</div>
        </div>
      </div>
    </q-header>

    <q-drawer
        v-model="leftDrawerOpen"
        show-if-above
        :width="250"
        :breakpoint="600"
      >
        <q-scroll-area style="height: calc(100% - 192px); margin-top: 192px; border-right: 1px solid #ddd">
          <q-list padding>
            <q-item
            to="/"
            exact
            clickable 
            v-ripple>
              <q-item-section avatar>
                <q-icon name="list" />
              </q-item-section>

              <q-item-section>
                Todo
              </q-item-section>
            </q-item>

           <q-item
           to="/help" 
           exact
           clickable 
           v-ripple>
              <q-item-section avatar>
                <q-icon name="help" />
              </q-item-section>

              <q-item-section>
                Help
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>

        <q-img class="absolute-top" src="statics/mountain.jpg" style="height: 192px">
          <div class="absolute-bottom bg-transparent">
            <q-avatar size="56px" class="q-mb-sm">
              <img src="statics/2570013.jpg">
            </q-avatar>
            <div class="text-weight-bold">Hong Jin Gi</div>
            <div>@jingi</div>
          </div>
        </q-img>
      </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import {date} from 'quasar'

export default {
  name: 'MyLayout',

  data() {
    return {
      leftDrawerOpen: false
    }
  },
  computed: {
    todaysDate() {
      let timeStamp = Date.now()
      return date.formatDate(timeStamp, 'dddd D MMMM')
    }
  },
  methods: {
    toggleLeftDrawer() {
      this.leftDrawerOpen = !this.leftDrawerOpen
    }
  }
}

</script>



<!-- <style lang="scss">
.q-header {
  // padding: 0;
  // margin: 0;
  position: relative;   // 자식 요소의 absolute 위치 기준점
  overflow: hidden;     // 내용이 헤더 밖으로 넘치지 않도록
  min-height: 200px;    // 헤더의 최소 높이 설정 (이미지 높이와 같게)
  // Quasar의 q-header는 기본 높이가 있지만, 배경 이미지와 콘텐츠를 포함하기 위해 명시적으로 최소 높이를 지정하는 것이 좋습니다.
}

.header-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;       // 부모(.q-header)의 높이를 따라감. '100'에서 '100%'로 변경!
  object-fit: cover;  // 이미지가 영역을 채우도록
  z-index: 0;         // 콘텐츠 뒤에 위치 (이전의 -1은 다른 모든 요소를 가려버리는 문제)
  opacity: 0.2;
  filter: grayscale(100%);
}

.q-header-content {
  position: absolute; // 헤더 전체를 덮도록 absolute 설정
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;       // 부모(.q-header)의 높이를 따라감
  z-index: 1;         // 이미지 위에 위치
  background: rgba(0, 0, 0, 0.2); // 이미지 위에 살짝 어두운 오버레이 (선택 사항)
  display: flex;
  flex-direction: column;
  justify-content: space-between; // 툴바와 텍스트를 위아래로 분리
}

.q-toolbar {
  background: transparent; // 툴바 배경을 투명하게 하여 이미지 비치도록
  color: white; // 툴바 텍스트(Quasar App, 버전) 색상을 흰색으로
}

// 'Todo' 텍스트와 날짜도 이미지 위에서 잘 보이도록
.q-px-lg.q-pt-xl.q-mb-md {
  color: white; // 텍스트 색상을 흰색으로
}
</style> -->

<style lang="scss">
  .header-image{
    height: 100%;
    z-index: -1;
    opacity: 0.2;
    filter: grayscale(100%);
  }
</style>
<template>
	<v-app>
		<!-- 툴바에 제목, 버튼을 삽입 -->
		 <v-navigation-drawer app v-model="drawer" :width="180" style="background-color: #6A5ACD">
    <v-list-item>
        <v-list-item-content align="left">
            <v-img to="/" contain height="45" width="80" style="text-decoration: none;" src="./assets/mainlogo.png"></v-img>	
          <v-list-item-title>
          </v-list-item-title>
          <v-divider></v-divider>
        </v-list-item-content>
      </v-list-item>
      <v-list dense nav>
          <v-list-item v-for="(item, i) in items" :key="i" :to="{ name: item.link }" link>
          <v-list-item-icon>
            <v-icon size="25" class="">{{item.icon}}</v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title style="font-size: 15px;font: bolder;font-weight: bolder;">{{item.text}}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
  </v-navigation-drawer>
		<v-app-bar color="blue-grey" dark app fixed>
			<v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
			<v-toolbar-title>내방반출시스템</v-toolbar-title>
			<v-spacer></v-spacer>
			<v-btn icon>
				<v-icon>more_vert</v-icon>
			</v-btn>
		</v-app-bar>
		<v-content>
			<!-- 카드 그리드 사이에 여백 설정-->
			<v-container>
				<v-row>
					<!-- 기기별로 그리드의 크기 설정-->
					<v-col cols="12" sm="6" md="4" lg="3" xl="2" v-for="item in this.aPictures" :key=item.key>
						<!-- 카드 UI에 사진 담아내기-->
						<v-card height="330px">
							<v-img :src="item.url" height="200px">
							</v-img>
							<v-card-title>
								<h1 class="title grey--text text--darken-3 
									mb-3">{{item.title}}</h1>
								<p class="body-2 grey--text">{{item.info}}</p>
							</v-card-title>
						</v-card>
					</v-col>
				</v-row>
			</v-container>
		</v-content>
		<!-- 바닥글 고정 -->
		<v-footer fixed>
			<div class="mx-auto">&copy;Hanamicron</div>
		</v-footer>
	</v-app>
</template>

<script>
	// 사진 정보(JSON 파일) 읽어오기
	import oPictureData from '@/datasources/picture-data'
	export default {
		data() {
			return {
				// aPictures의 배열에 사진 정보 저장하기
				'aPictures': oPictureData.aPictures,
				items: [
						{
						icon: 'mdi-calendar-clock',
						text: '발송 현황',
						link: 'report'
						},
						{
						icon: 'mdi-file-cog',
						text: '발송 설정',
						link: 'settings'
						}
					],
					drawer: null
			}
		},
		name: 'App',
	}
</script>
<style>
.itemtitle {
  font-size: 10px;
}
.no-background-hover::before {
  background-color: transparent !important;
}
</style>
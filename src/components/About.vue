<script setup xmlns="http://www.w3.org/1999/html">
import WelcomeItem from './WelcomeItem.vue'
import DocumentationIcon from './icons/IconDocumentation.vue'
import ToolingIcon from './icons/IconTooling.vue'
import EcosystemIcon from './icons/IconEcosystem.vue'
import CommunityIcon from './icons/IconCommunity.vue'
import SupportIcon from './icons/IconSupport.vue'
</script>
<template>
  <div class="contents-box">
    <div class="about-box">
      <h2>#About</h2>
      <div class="about-content">
        アプリケーションエンジニアをしているエイジの個人ブログです。
        技術的なことや趣味の話を書いています。
        毎週日曜日の20時に更新する予定です。
        本ブログでは下記のような内容がよく話題に出ます。<br>
        ・プログラミング(主にサーバーサイド)<br>
        ・コーヒー<br>
        ・バイク<br>
      </div>
    </div>

    <div class="profile-box">
      <h2>#Profile</h2>
      <div class="profile-content">
        バックエンドエンジニアをしています。
        業務ではメインでJava×Springを使用しています。
        特に私の業務領域においては高い品質が求められるため、
        E2Eテストのフレームワークも自分たちで作成運用する必要があり、それをPythonで作ったりもしています。<br>
        <h3>技術スタック</h3>
        バックエンド<br>
        　・Java(Spring)<br>
        　・Golang(業務(勉強中))<br>
        　・Python<br>
        フロントエンド<br>
        　・HTML/CSS<br>
        　・TypeScript<br>
        　・Angular(業務(勉強中))<br>
        　・Vue.js(趣味)<br>
      </div>
    </div>
  </div>

</template>

<style>
@media (min-width: 1024px) {
  .contents-box{
    width:800px;
    margin: 0 auto;
  }
  .about-box {
    /*align-items: center;*/
    padding-top: 20px;
    padding-left: 20px;
    padding-right: 20px;
    padding-bottom: 10px;
  }

  .profile-box {
    /*align-items: center;*/
    padding-top: 10px;
    padding-left: 20px;
    padding-right: 20px;
    padding-bottom: 20px;
  }

}
</style>

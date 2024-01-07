<script>


  // 모듈 import 
  import Header from "./components/main/Header.svelte";
  import Nav from "./components/main/Nav.svelte";
  import Contents_Mid from "./components/main/Contents_Mid.svelte";
  import Footer from "./components/main/Footer.svelte";
  import Section from "./components/main/Section.svelte";
  import Article from "./components/main/Article.svelte";
  import ContentsTop from "./components/main/Contents_Top.svelte";


  // 탭 클릭 이벤트 정의
  import { onMount } from "svelte";
  let activeTabIndex = 0; // 초기값 부여
  onMount(() => {
    // You can add any initialization logic here
  });
  function activateTab(index) {
    activeTabIndex = index;
  }

  // 탭 변경시 페이드 효과를 위한 변수
  let fadeIn = true;

</script>

<style>
  main {
    max-width: 1000px;
    margin: 0 auto; /* 가운데 정렬을 위해 사용 */
    width: 100%; /* 부모의 100% 폭을 사용 */
  }
</style>


<!------------------------------------------------------------------------------------------------------------------------------------------------------------------->
<!-- HTML 영역 -->
<!------------------------------------------------------------------------------------------------------------------------------------------------------------------->



<main>
  
  <header>
    <Header />
  </header>

  <ContentsTop />

  <div role="tablist" class="tabs tabs-boxed">
    {#each [0, 1] as tab, tabIndex (tab)}
      <a
        role="tab"
        class={`tab ${activeTabIndex === tabIndex ? 'tab-active' : ''}`}
        on:click={() => activateTab(tabIndex)}
      >
        <!-- Update the tab names here -->
        {#if tab === 0}
          고(高)마진 상품
        {:else if tab === 1}
          핫(hot)마진 상품
        {/if}
      </a>
    {/each}
  </div>

  <!--탭클릭 변경 이벤트-->
  {#if activeTabIndex === 0}
  <!--Tab 0 : 고마진상품-->
    <Contents_Mid />
  {:else if activeTabIndex === 1}
  <!--Tab 1 : Hot 상품-->
    <Section />
    <Article />
  {:else if activeTabIndex === 2}
  {/if}

  <Footer />
</main>
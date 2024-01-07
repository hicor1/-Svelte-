<script>
  let tableData = [
  {제품명: '나이키 줌 보메로 5 프리미엄 라이트 아이언 오어 앤 플랫 퓨터', 옵션: '230', 즉시구매가격: 190000, 보관판매가격: '없음', 마진율:100.0, Net마진율:100, 총판매량:14379, 최근7일체결량:30},
  {제품명: '나이키 줌 보메로 5 프리미엄 라이트 아이언 오어 앤 플랫 퓨터', 옵션: '230', 즉시구매가격: 290000, 보관판매가격: '없음', 마진율:57.1, Net마진율:51, 총판매량:333, 최근7일체결량:10},
  {제품명: '나이키 줌 보메로 5 프리미엄 라이트 아이언 오어 앤 플랫 퓨터', 옵션: '230', 즉시구매가격: 390000, 보관판매가격: '없음', 마진율:32.7, Net마진율:27, 총판매량:222, 최근7일체결량:3},
    ];
  let sortColumn = null;
  let sortDirection = null;

  // 제품명이 너무길면 자르는 코드
  function trimText(text, maxLength) {
    return text.length > maxLength ? text.slice(0, maxLength) + '...' : text;
  }

  // 정렬 기능 코드
  function sortBy(column) {
    // 정렬 방향 업데이트
    if (sortColumn === column) {
      // 클릭한 열이 현재 정렬 중인 열일 경우 방향 전환
      sortDirection = sortDirection === 'asc' ? 'desc' : 'asc';
    } else {
      // 클릭한 열이 다른 열일 경우 기본 오름차순 설정
      sortColumn = column;
      sortDirection = 'asc';
    }

    // 데이터 정렬
    tableData = tableData.sort((a, b) => {
      const aValue = a[sortColumn];
      const bValue = b[sortColumn];

      if (sortDirection === 'asc') {
        return aValue < bValue ? -1 : aValue > bValue ? 1 : 0;
      } else {
        return bValue < aValue ? -1 : bValue > aValue ? 1 : 0;
      }
    });
  }

  // 미니그래프 넣는 코드
  function generateMiniGraph(value) {
    // Define color gradient range
    const minColor = [144, 238, 144]; // Light green
    const maxColor = [0, 128, 0];     // Dark green

    // Calculate color based on the value
    const normalizedValue = Math.min(Math.max(value, 0), 100); // Normalize value between 0 and 100
    const color = minColor.map((min, i) => {
      const max = maxColor[i];
      return Math.round(min + (max - min) * (normalizedValue / 100));
    });

    // Convert RGB values to CSS color
    const cssColor = `rgb(${color.join(',')})`;

    // Return the colored div
    return `<div style="width: ${normalizedValue}px; height: 10px; background-color: ${cssColor};"></div>`;
  }

  //세자리마다 콤마 찍는 코드
  function numberWithCommas(x) {
    return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
  }

</script>


<!------------------------------------------------------------------------------------------------------------------------------------------------------------------->
<!-- HTML 영역 -->
<!------------------------------------------------------------------------------------------------------------------------------------------------------------------->

<div class="overflow-x-auto max-w-full mt-9">
  <table class="table w-full">
    <!-- head -->
    <thead>
      <tr>
        <th><button on:click={() => sortBy('제품명')}>제품명 {sortColumn === '제품명' && sortDirection === 'asc' ? '↑' : '↓'}</button></th>
        <th><button on:click={() => sortBy('옵션')}>옵션 {sortColumn === '옵션' && sortDirection === 'asc' ? '↑' : '↓'}</button></th>
        <th><button on:click={() => sortBy('즉시구매가격')}>즉시구매가격 {sortColumn === '즉시구매가격' && sortDirection === 'asc' ? '↑' : '↓'}</button></th>
        <th><button on:click={() => sortBy('보관판매가격')}>보관판매가격 {sortColumn === '보관판매가격' && sortDirection === 'asc' ? '↑' : '↓'}</button></th>
        <th><button on:click={() => sortBy('마진율')}>마진율(%){sortColumn === '마진율' && sortDirection === 'asc' ? '↑' : '↓'}</button></th>
        <th><button on:click={() => sortBy('Net마진율')}>Net마진율(%){sortColumn === 'Net마진율' && sortDirection === 'asc' ? '↑' : '↓'}</button></th>
        <th><button on:click={() => sortBy('총판매량')}>총판매량 {sortColumn === '총판매량' && sortDirection === 'asc' ? '↑' : '↓'}</button></th>
        <th><button on:click={() => sortBy('최근7일체결량')}>최근7일체결량 {sortColumn === '최근7일체결량' && sortDirection === 'asc' ? '↑' : '↓'}</button></th>
        
      </tr>
    </thead>
    <tbody>
      {#each tableData as row}
        <tr class="hover">
          <td>{trimText(row.제품명, 30)}</td>
          <td>{row.옵션}</td>
          <td>{numberWithCommas(row.즉시구매가격)}</td>
          <td>{row.보관판매가격}</td>
          <td>{row.마진율}</td>
          <td>{row.Net마진율}</td>
          <td>{numberWithCommas(row.총판매량)}</td>
          <td>
            <div style="display: flex; align-items: center;">
              <span style="margin-right: 5px;">{row.최근7일체결량}</span>
              {@html generateMiniGraph(row.최근7일체결량)}
            </div>
          </td>
        </tr>
      {/each}
    </tbody>
  </table>
</div>

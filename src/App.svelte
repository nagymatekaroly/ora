<script>
    
    var time = new Date();
    $: [or, p, mp] = time.toLocaleTimeString().split(":").map(Number);

    
    setInterval(() => (time = new Date()), 1000);

    
    const fx = (t, r, o) => 250 + r * Math.cos((t * Math.PI) / (o / 2) - Math.PI / 2);
    const fy = (t, r, o) => 250 + r * Math.sin((t * Math.PI) / (o / 2) - Math.PI / 2);
</script>

<main>
    <svg width="500" height="500">
        
        <circle cx="250" cy="250" r="240" fill="#ffffff" stroke="white" stroke-width="5" />
        <circle cx="250" cy="250" r="230" fill="#333333" stroke="darkgrey" stroke-width="4" />

        
    
        {#each Array.from({ length: 60 }) as _, i}
        {#if i % 5}
          <line
            x2={fx(i, 214, 60)}
            y2={fy(i, 214, 60)}
            x1={fx(i, 220, 60)}
            y1={fy(i, 220, 60)}
            stroke="red"
            stroke-width="2"
          />
        {:else}
          <circle
            cx={fx(i, 180, 60)}
            cy={fy(i, 180, 60)}
            r="30"
            fill="black"
            stroke="red"
            stroke-width="2"
          />
          <circle
            cx={fx(i, 218, 60)}
            cy={fy(i, 218, 60)}
            r="6"
            fill="whiteblack"
            stroke="red"
            stroke-width="2"
          />
        {/if}
      {/each}
      {#each Array.from({ length: 12 }) as _, i}
        <text
          x={fx(i, 180, 12)}
          y={fy(i, 180, 12) - 1}
          fill="white"
          text-anchor="middle"
          dominant-baseline="central"
          font-size="40">{i == 0 ? 12 : i}</text
        >
      {/each}
      <line
        x2={fx(p + mp / 60, 190, 60)}
        y2={fy(p + mp / 60, 190, 60)}
        class="osz"
        x1="250"
        y1="250"
        stroke="black"
        stroke-width="6"
      />
      <line
        x2={fx(or * 5 + p / 12, 146, 60)}
        y2={fy(or * 5 + p / 12, 146, 60)}
        x1="250"
        y1="250"
        stroke="red"
        stroke-width="10"
      />
      <circle
        cx="250"
        cy="250"
        r="10"
        fill="white"
        stroke="black"
        stroke-width="6"
      />
      <line
        x2={fx(mp, 210, 60)}
        y2={fy(mp, 210, 60)}
        x1={fx(mp, -20, 60)}
        y1={fy(mp, -20, 60)}
        stroke="darkgrey"
        stroke-width="4"
        class="osz"
      />

        

    </svg>
</main>

<style>
    .osz {
        filter: drop-shadow(0px 0px 2px rgb(0 0 0 / 1));
        filter: opacity(100%);
        color: white;
    }
</style>
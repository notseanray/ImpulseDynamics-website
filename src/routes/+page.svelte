<script>
	import Counter from './Counter.svelte';
	import welcome from '$lib/images/svelte-welcome.webp';
	import welcome_fallback from '$lib/images/svelte-welcome.png';
</script>

<svelte:head>
	<title>Impulse Dynamics - About</title>
	<meta name="description" content="Impulse Dynamics - About" />
</svelte:head>

<section>
	<div class="text-[#c9c9c9] uppercase font-bold text-2xl">
        we are
        <div class="text-[#eb5060] font-thin text-4xl">
            impulse dynamics
        </div>
	</div>
    <div class="flex">
        <div class="graph__wrapper">
          <svg width="315px" height="107px" viewBox="0 0 315 107" version="1.1" style="overflow:visible">
            <g  id="Page-1" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd" sketch:type="MSPage">

              <path id="Path-1" class="path" fill="none" stroke="#c9c9c9" stroke-width="3" stroke-linejoin="round" stroke-miterlimit="10" d="M489,11,211.5,41,5s172.5-24.5,86,57,0,2.1c0,0,1.4"/>

              <polyline id="arrow" points="0,-9 18,0 0,9,5,0" fill="#c9c9c9">
                <animateMotion rotate="auto" begin="1s" dur="1.6s" repeatCount="1" fill="freeze">
                  <mpath xlink:href="#Path-1" />
                </animateMotion>
              </polyline>

            </g>
          </svg>
            <div class="dot" />
        </div>
    </div>
</section>

<style>
.dot {
    height: 12vw;
    width: 12vw;
    background-color: #eb5060;
    border-radius: 50%;
    display: inline-block;
}
.path { stroke-dasharray: 1000; stroke-dashoffset: 1000; animation: dash 2s linear forwards; animation-iteration-count: 1;}
@keyframes dash {
  to {
    stroke-dashoffset: 0;
  }
}
.dashed{
  stroke-dasharray: 5,12;

}
#arrow{animation: arrow 1s linear forwards; opacity:0;}
@keyframes arrow {
  to {
    opacity: 1;
  }
}
.ifrm{border:none; width:100%;margin-top:50px;}
</style>

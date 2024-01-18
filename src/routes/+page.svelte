<script>
	import Counter from "./Counter.svelte";
</script>


  <div class="... flex items-center justify-center ">
	<h1 class=" header italic font-bold  top-2 left-2 ">
		Calculator
	  </h1>
  </div>
  
  <style lang="postcss">
	:global(html) {
	  background-color: theme(colors.gray.300);
	}
	.header{
		font-size: 55px ;/*3.75rem */
        line-height: 1;
		width: 300px; /* 384px */
		border:1px solid #eee;
        box-shadow: 2px 2px 2px #eee;
		padding: 15px;
		color: rgb(27, 10, 13);
	}
  </style>

<Counter/>
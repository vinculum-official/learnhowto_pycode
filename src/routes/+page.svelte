<script lang="ts">
  import Repl from '$lib/Repl.svelte';

  let sidebarOpen = $state(true);
  let selectedLesson = $state(0);
</script>

<svelte:head>
    <link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined" rel="stylesheet" />
</svelte:head>

<!-- +page.svelte or layout -->
<div class="flex h-screen overflow-hidden">

  <!-- Left sidebar -->
 <div class={`grid transition-all duration-300 shrink-0 ${sidebarOpen ? 'grid-cols-[400px]' : 'grid-cols-[0px]'}`}>
  <div class="overflow-hidden flex-col gap-3">
  <button onclick={() => sidebarOpen = !sidebarOpen} class="material-symbols-outlined">
  close
</button>
    
    <!-- pycode header -->
        <div class="p-4 mb-5">
        <h1 class="text-3xl font-bold mb-px italic">learn how to <strong class="underline decoration-solid italic">pycode</strong></h1>
        <p class="text-md text-gray-700">Python for absolute beginners</p>
        <hr class="my-2 border-neutral-300" />
        </div>
        <!-- lessons list -->
        <div class="p-4 overflow-y-auto">
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 1 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 1}>Lesson 1: "Hello, World!"</button> <br />
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 2 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 2}>Lesson 2: What's a Syntax?</button> <br />
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 3 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 3}>Lesson 3: Comments (in code)</button>
            <hr>
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 4 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 4}>Lesson 4: Variables, Statements and Operators</button>
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 5 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 5}>Lesson 5: Input</button> <br />
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 6 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 6}>Lesson 6: Output</button>
            <hr>
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 7 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 7}>Lesson 7: Choices (if/else)</button> <br />
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 8 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 8}>Lesson 8: Loops</button>
            <hr>
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 9 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 9}>Set up Python on your computer</button> <br />
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 10 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 10}>Think like a programmer</button>
        </div>
        </div>

  </div>

    <!-- Main content -->
    <div class="flex-1 rounded-2xl bg-neutral-100 overflow-y-auto relative">
    {#if !sidebarOpen}
      <div class="absolute top-4 left-4">
        <button onclick={() => sidebarOpen = !sidebarOpen} class="material-symbols-outlined">
  menu
</button>
      </div>
    {/if}
      <div class="p-6 ml-10 mr-10">
    {#if selectedLesson == 0}

    <h1 class="text-3xl font-bold">Hello!</h1>
    <p>This is <span class="italic">learn how to <strong class="underline decoration-solid">pycode</strong></span>, a website for absolute beginners in Python! This website was created by <a class="underline decoration-solid text-blue-600" href="https://maniksharma.xyz/">me</a>! for people who don't know Python. To learn, simply follow the 10 lessons, and code! You can code in the browser, Thanks to <a class="underline decoration-solid text-blue-600" href="https://skulpt.org/">Skulpt</a>. Simply click on a lesson to start learning!</p>
    
    {/if}

    {#if selectedLesson == 1}
    <h1 class="text-3xl font-bold mb-5">"Hello, World!"</h1>
    <p>Welcome to your first Python lesson! In this lesson, you'll learn how to print "Hello, World!" to the screen.</p>
    <br />
    <p>Hello, World is the first thing anyone does when learning a programming language. In Python, this is quite easy. All you have to do is use the <code class="px-1 py-0.5 bg-neutral-300 text-orange-600 rounded-md text-sm">print()</code> function.</p>
    <br />
    <p>For Python, printing the text "Hello, World!" looks like this:</p>
    <br />
    <pre class="bg-neutral-300 p-4 rounded-md text-sm overflow-x-auto"><span class="text-orange-600">print</span><span class="text-blue-700">(</span><span class="text-neutral-800">"Hello, World!"</span><span class="text-blue-500">)</span></pre>
    <br />
    <p>Try it out in the code editor below! You can change the text to print something else, or even print multiple things! (Try changing the text inside the quotes, duplicating the line, whatever you want!)</p>
    <br />
    <Repl defaultCode={`print("Hello, World!")`} />
    <br />
    <p>After you're done, click on the next lesson!</p>
    {/if}
    {#if selectedLesson >= 2}
    <h1>coming soon!</h1>
    {/if}
    </div> 

  </div>

</div>

<style>
.material-symbols-outlined {
  font-variation-settings:
  'FILL' 0,
  'wght' 400,
  'GRAD' 0,
  'opsz' 24
}
</style>
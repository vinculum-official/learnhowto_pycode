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
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 4 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 4}>Lesson 4: Variables</button> <br />
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 11 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 11}>Lesson 5: Operators</button> <br />
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 5 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 5}>Lesson 6: Input and Output</button>
            
            <hr>
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 7 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 7}>Lesson 7: Choices (if/else)</button> <br />
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 8 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 8}>Lesson 8: Loops</button> <br />
            <button class="mb-2 cursor-pointer hover:text-blue-600 {selectedLesson === 6 ? 'font-bold text-blue-600' : ''}" onclick={() => selectedLesson = 6}>Lesson 9: Functions</button>
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
    <p>Welcome to your first Python lesson! In this lesson, you'll learn how to print "Hello, World!" to the screen, and learn a bit about Python!</p>
    <br /><br />
    <p>Python was created by Guido van Rossum and first released in 1991. It is an interpreted language, meaning that it excecutes code line-by-line, as it was written.</p>
    <br />
    <p>Hello, World is the first thing anyone does when learning a programming language. In Python, this is quite easy. All you have to do is use the <code class="px-1 py-0.5 bg-neutral-300 text-orange-600 rounded-md text-sm">print()</code> function.</p>
    <p>For Python, printing the text "Hello, World!" looks like this:</p>
    <br />
    <pre class="bg-neutral-300 p-4 rounded-md text-sm overflow-x-auto"><span class="text-orange-600">print</span><span class="text-blue-700">(</span><span class="text-neutral-800">"Hello, World!"</span><span class="text-blue-500">)</span></pre>
    <br />
    <h2 class="text-xl font-semibold mt-6 mb-2">Try it yourself!</h2>
    <p>Try it out in the code editor below! You can change the text to print something else, or even print multiple things! (Try changing the text inside the quotes, duplicating the line, whatever you want!)</p>
    <Repl defaultCode={`print("Hello, World!")`} />
    <br />
    <p>After you're done, click on the next lesson!</p>
    {/if}
    {#if selectedLesson == 2}
    <h1 class="text-3xl font-bold mb-5">What's a Syntax?</h1>
    <p>Syntax is the set of rules that define how a programming language should be written. In Python, syntax is quite simple and readable. Here are a few basic rules:</p> <br />
    <ul>
      <li>- Python uses indentation to define code blocks.</li>
      <li>- Comments in Python start with a # symbol. More about this in the next lesson.</li>
      <li>- Variables are assigned using the = operator. More about this in lesson 4.</li>
      <li>- If you are writing a string, it must be enclosed in quotes. (Single or double, Python doesn't care. Just be even with it!)</li>
      <li>- Python is case-sensitive. This means <code class="px-1 py-0.5 bg-neutral-300 text-orange-600 rounded-md text-sm">print()</code> and <code class="px-1 py-0.5 bg-neutral-300 text-orange-600 rounded-md text-sm">Print()</code> are different.</li>
    </ul>
    <br />
    <h2 class="text-xl font-semibold mt-6 mb-2">Try it yourself!</h2>
    <p>Spot the errors in the code!</p>
    <Repl defaultCode={`Print(Hello, World!)`} />
    <br />
      <p>After you're done, click on the next lesson!</p>
    {/if}
    {#if selectedLesson == 3}
    <h1 class="text-3xl font-bold mb-5">Comments (in code)</h1>
    <p>Comments are lines of code ignored by the interpreter, and so that are not executed by the computer.  They are used to explain what the code does, or to leave notes for other programmers (or yourself in the future!). In Python, comments start with a # symbol (as told in lesson 2). Anything after the # symbol on that line is considered a comment and is ignored by the computer. Make sure to <strong>only comment on sections on code where explaination is needed.</strong></p>
    <p>An example of a bad comment in Python:</p>
    <br />
    <pre class="bg-neutral-300 p-4 rounded-md text-sm overflow-x-auto"><span class="text-orange-600">print</span><span class="text-blue-700">(</span><span class="text-neutral-800">"Hello, World!"</span><span class="text-blue-500">)</span><span class="text-green-700"> # This prints hello world to the terminal</span></pre>
    <br />
    <p>While this is an example of a good comment:</p>
    <pre class="bg-neutral-300 p-4 rounded-md text-sm overflow-x-auto"><span class="text-orange-600">print</span><span class="text-blue-700">(</span><span class="text-neutral-800">"Hello, World!"</span><span class="text-blue-500">)</span><span class="text-green-700"> # First test to check if Python is working</span></pre>
    <br />
    <p>The reason the first one was a bad comment, is that it did not add anything. We know, that it will print Hello World. But the second one is giving extra information - "First test of Python" is telling us more than what the code does. Though, if you have a complicated section of code, explaining the code in a comment is also a good comment.</p>
    <h2 class="text-xl font-semibold mt-6 mb-2">Try it yourself!</h2>
    <p>Comment the code!</p>
    <Repl defaultCode={`print("Hello, World!")`} />
    {/if}
    {#if selectedLesson == 4}
    <h1 class="text-3xl font-bold mb-5">Variables</h1>

<p>So far, you've been printing text directly. But what if you want to store something and use it later?</p>

<p>This is where <strong>variables</strong> come in.</p>

<br />

<p>A variable is like a container that stores a value. This value is stored in memory, and to access it, you "call" the variable by the name you gave it (eg: name, age, dob etc.) Also, names should be descriptive, so a good name is "age" for getting an age and not "a", "b", "c" or "d". While making a good name might take a few seconds, it is very important for understanding code later on.</p>

<p>In Python, you create a variable using the <code class="px-1 py-0.5 bg-neutral-300 text-orange-600 rounded-md text-sm">=</code> operator.</p>

<br />

<pre class="bg-neutral-300 p-4 rounded-md text-sm overflow-x-auto">
name = "Alex"
</pre>

<br />

<p>Here, we are storing the text <code class="px-1 py-0.5 bg-neutral-300 text-orange-600 rounded-md text-sm">"Alex"</code> in a variable called <code class="px-1 py-0.5 bg-neutral-300 text-orange-600 rounded-md text-sm">name</code>.</p>

<p>We can now use this variable in our code:</p>

<br />

<pre class="bg-neutral-300 p-4 rounded-md text-sm overflow-x-auto">
name = "Alex"
print(name)
</pre>

<br />

<p>This will print:</p>

<pre class="bg-neutral-300 p-4 rounded-md text-sm overflow-x-auto">
Alex
</pre>

<br />

<p>You can also change the value of a variable:</p>

<pre class="bg-neutral-300 p-4 rounded-md text-sm overflow-x-auto">
name = "Alex"
name = "Sam"
print(name)
</pre>

<br />

<p>The output will now be:</p>

<pre class="bg-neutral-300 p-4 rounded-md text-sm overflow-x-auto">
Sam
</pre>

<br />

<h2 class="text-xl font-semibold mt-6 mb-2">Using Variables with Numbers</h2>

<p>Variables can also store numbers:</p>

<pre class="bg-neutral-300 p-4 rounded-md text-sm overflow-x-auto">
age = 15
print(age)
</pre>

<br />

<p>You can even do math with them:</p>

<pre class="bg-neutral-300 p-4 rounded-md text-sm overflow-x-auto">
a = 5
b = 3
print(a + b)
</pre>

<br />

<h2 class="text-xl font-semibold mt-6 mb-2">Try it yourself!</h2>

<p>Try changing the values, creating new variables, or doing simple math.</p>

<Repl defaultCode={`name = "Your Name"
age = 15

print(name)
print(age)

# Try changing the values or adding math below
`} />

<br />

<p>After you're done, click on the next lesson!</p>
    {/if}
    {#if selectedLesson == 11}
    <h1 class="text-3xl font-bold mb-5">Operators</h1>

<p>Operators are symbols that perform actions on values.</p>

<p>You’ve already seen one before:</p>

<pre class="bg-neutral-300 p-4 rounded-md text-sm overflow-x-auto">
print(5 + 3)
</pre>

<p>Here, the <code class="px-1 py-0.5 bg-neutral-300 text-orange-600 rounded-md text-sm">+</code> is an operator. It adds two values.</p>

<br />

<h2 class="text-xl font-semibold mt-6 mb-2">Basic Math Operators</h2>

<ul>
  <li>- <code>+</code> → addition</li>
  <li>- <code>-</code> → subtraction</li>
  <li>- <code>*</code> → multiplication</li>
  <li>- <code>/</code> → division</li>
</ul>

<br />

<pre class="bg-neutral-300 p-4 rounded-md text-sm overflow-x-auto">
a = 10
b = 5

print(a + b)
print(a - b)
print(a * b)
print(a / b)
</pre>

<br />

<h2 class="text-xl font-semibold mt-6 mb-2">Comparison Operators</h2>

<p>These compare values and return either <strong>True</strong> or <strong>False</strong>.</p>

<ul>
  <li>- <code>==</code> → equal to</li>
  <li>- <code>!=</code> → not equal to</li>
  <li>- <code>&gt;</code> → greater than</li>
  <li>- <code>&lt;</code> → less than</li>
</ul>

<br />

<pre class="bg-neutral-300 p-4 rounded-md text-sm overflow-x-auto">
print(5 == 5)
print(5 != 3)
print(10 > 3)
</pre>

<br />

<h2 class="text-xl font-semibold mt-6 mb-2">Logical Operators</h2>

<p>These are used to combine conditions.</p>

<ul>
  <li>- <code>and</code></li>
  <li>- <code>or</code></li>
  <li>- <code>not</code></li>
</ul>

<br />

<pre class="bg-neutral-300 p-4 rounded-md text-sm overflow-x-auto">
print(5 > 3 and 2 &lt; 4)
print(not True)
</pre>

<br />

<h2 class="text-xl font-semibold mt-6 mb-2">Important Note</h2>

<p>In some other programming languages, you might see:</p>

<ul>
  <li>- <code>&&</code> instead of <code>and</code></li>
  <li>- <code>||</code> instead of <code>or</code></li>
  <li>- <code>!</code> instead of <code>not</code></li>
</ul>

<p>But in Python, you must use <strong>words</strong> instead.</p>

<br />

<h2 class="text-xl font-semibold mt-6 mb-2">Try it yourself!</h2>

<Repl defaultCode={`a = 10
b = 5

print(a + b)
print(a > b)
print(a > b and b < 10)
`} />

<br />

<p>After you're done, click on the next lesson!</p>
    {/if}
    {#if selectedLesson >= 5}
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
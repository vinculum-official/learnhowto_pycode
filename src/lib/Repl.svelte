<script lang="ts">
  let { defaultCode } = $props();

  let code = $state(defaultCode);
  let output = $state('');
  let isError = $state(false);
  let hasRun = $state(false);

  const Sk: any = (window as any).Sk;

  function run() {
    const currentCode = code;

    output = '';
    isError = false;
    hasRun = true;

    let result = '';

    Sk.configure({
      output: (t: string) => { result += t; },
      read: (f: string) => {
        if (Sk.builtinFiles?.files[f] === undefined)
          throw new Error(`File not found: ${f}`);
        return Sk.builtinFiles.files[f];
      },
      inputfun: (prompt: string) => window.prompt(prompt) ?? '',
      inputfunTakesPrompt: true,
    });

    Sk.misceval.asyncToPromise(() =>
      Sk.importMainWithBody('<stdin>', false, currentCode, true)
    ).then(() => {
      output = result || '(no output)';
    }).catch((e: any) => {
      output = e.toString();
      isError = true;
    });
  }

  function reset() {
    code = defaultCode;
    output = '';
    hasRun = false;
    isError = false;
  }
</script>

<div class="rounded-md overflow-hidden border border-neutral-300 my-4">
  <!-- Editor -->
  <div class="bg-neutral-800 p-1 flex justify-between items-center px-3">
    <span class="text-neutral-400 text-xs">Python</span>
    <div class="flex gap-2">
      <button
        onclick={reset}
        class="text-xs text-neutral-400 hover:text-white px-2 py-1 rounded"
      >reset</button>
      <button
        onclick={run}
        class="text-xs bg-orange-500 hover:bg-orange-600 text-white px-3 py-1 rounded"
      >run</button>
    </div>
  </div>

  <textarea
    bind:value={code}
    spellcheck="false"
    class="w-full bg-neutral-900 text-neutral-100 p-4 text-sm font-mono resize-y min-h-24 outline-none"
  ></textarea>

  <!-- Output -->
  {#if hasRun}
    <div class="border-t border-neutral-700 bg-neutral-950 p-4 font-mono text-sm whitespace-pre-wrap {isError ? 'text-red-400' : 'text-green-300'}">
      {output}
    </div>
  {/if}
</div>
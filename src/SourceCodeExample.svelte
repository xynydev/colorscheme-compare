<main>
<pre>
<div class="comment">
// Code from https://github.com/id-Software/DOOM

//
// Z_Free
//</div>
<div class="keyword">void</div> <div class="function">Z_Free</div> (<div class="keyword">void</div>* ptr)
&#123;
    <div class="string">memblock_t</div>*		block;
    <div class="string">memblock_t</div>*		other;
    
    block = (<div class="string">memblock_t</div> *) ( (byte *)ptr - sizeof(<div class="string">memblock_t</div>));

    <div class="keyword">if</div> (block-&#155;id != ZONEID)
    <div class="function">I_Error</div> (<div class="string">&quot;Z_Free: freed a pointer without ZONEID&quot;</div>);
        
    <div class="keyword">if</div> (block-&#155;user &#155; (<div class="keyword">void</div> **)0x100)
    &#123;
    <div class="comment">// smaller values are not pointers
    // Note: OS-dependend?</div>
    
    <div class="comment">// clear the user&#39;s mark</div>
    *block-&#155;user = <div class="var">0</div>;
    &#125;

    <div class="comment">// mark as free</div>
    block-&#155;user = <div class="var">NULL</div>;	
    block-&#155;tag = <div class="var">0</div>;
    block-&#155;id = <div class="var">0</div>;
    
    other = block-&#155;prev;

    <div class="keyword">if</div> (<div class="keyword">!</div>other-&#155;user)
    &#123;
    <div class="comment">// merge with previous free block</div>
    other-&#155;size += block-&#155;size;
    other-&#155;next = block-&#155;next;
    other-&#155;next-&#155;prev = other;

    <div class="keyword">if</div> (block == mainzone-&#155;rover)
        mainzone-&#155;rover = other;

    block = other;
    &#125;
    
    other = block-&#155;next;
    <div class="keyword">if</div> (<div class="keyword">!</div>other-&#155;user)
    &#123;
    <div class="comment">// merge the next free block onto the end</div>
    block-&#155;size += other-&#155;size;
    block-&#155;next = other-&#155;next;
    block-&#155;next-&#155;prev = block;

    <div class="keyword">if</div> (other == mainzone-&#155;rover)
        mainzone-&#155;rover = block;
    &#125;
&#125;
</pre>
</main>

<style>
    .keyword {
        display: inline;
        color: var(--syntax-keyword);
    }

    .function {
        display: inline;
        color: var(--syntax-function);
    }

    .string {
        display: inline;
        color: var(--syntax-string);
    }

    .var {
        display: inline;
        color: var(--syntax-var);
    }

    .comment {
        display: inline;
        color: var(--syntax-comment);
    }
</style>
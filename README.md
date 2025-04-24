# comp2300-lab-6-solved



**<span style='color:red'>TO GET THIS SOLUTION VISIT:</span>** https://www.ankitcodinghub.com/product/comp2300-lab-6-solved/

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;74262&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;3&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (3 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;Comp2300 Lab 6 Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">
            
<div class="kksr-stars">
    
<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
    
<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">
            

<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>
                

<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (3 votes)    </div>
    </div>
Before you attend this week’s lab, make sure:

<ol>
<li>you can read and write basic assembly code: programs with registers, instructions, labels and branching</li>
<li>you have read the laboratory text below</li>
</ol>
In this week’s lab you will:

<ol>
<li>learn how to load and store with&nbsp;<code>ldr</code>&nbsp;and&nbsp;<code>str</code></li>
<li>blink the LEDs by reading &amp; writing special hardware registers</li>
<li>use&nbsp;<strong>functions</strong>&nbsp;to structure your code and remove duplication</li>
</ol>
Here’s a table of contents for this week’s lab, just in case you need to jump around.

<h2 id="introduction">Introduction</h2>
In this week’s lab you’ll read and write some of the special hardware registers on your discoboard to see&nbsp;<a class="acton-tabs-link-processed" href="https://en.wikipedia.org/wiki/Light-emitting_diode">LED</a>&nbsp;“output” from your program. Seeing stuff happen in the real world is a big part of the fun of microcontrollers, so this is going to be fun.

You’ll also start to see more clearly the connections between what we’ve been covering in this course and the higher-level programming languages you’re used to, with their&nbsp;<code>if</code>&nbsp;statements,&nbsp;<code>for</code>&nbsp;loops, and other niceties. This process of “demystifying” programming is a big part of what this course is about, so take the time to reflect on what you’re doing and how it fits in with what you know and do in other programming situations.

<h2 id="exercise-0-bit-shifting-practice">Exercise 0: bit shifting practice</h2>
Plug in your discoboard, fork &amp; clone the&nbsp;<a class="acton-tabs-link-processed" href="https://gitlab.cecs.anu.edu.au/comp2300/2021/comp2300-2021-lab-6">lab 6 template</a>&nbsp;to your machine, and open the&nbsp;<code>src/main.S</code>&nbsp;file as usual.

<p class="info-box">The stuff in Exercise 0 is all stuff we’ve covered already (in some cases as far back as week 2) but it’s sometimes good to have a warm-up/refresher. Feel free to jump straight to&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/labs/06-blinky/#using-labels">Exercise 1</a>&nbsp;if you’re feeling adventurous, but there’s no shame in taking your time and working through the warm-up stuff—practice makes perfect!

<h3 id="bit-shifting--logic-ops">Bit-shifting &amp; logic ops</h3>
You will need to use some logic operations in this lab, in particular, setting (set&nbsp;<code>1</code>) and clearing (set&nbsp;<code>0</code>) bits. This warm up exercise gives you a chance to practice bit shifting and using logic operations to set and clear bits.

Edit your&nbsp;<code>main.S</code>&nbsp;file so that it looks like the following. Don’t forget the required&nbsp;<code>.syntax unified</code>&nbsp;and&nbsp;<code>.global main</code>&nbsp;statements at the top of the file.

<pre><code class="language-ARM hljs"><span class="hljs-symbol">main</span>:
  <span class="hljs-keyword">ldr </span><span class="hljs-built_in">r0</span>, <span class="hljs-number">=0xcafe0000</span>
  <span class="hljs-keyword">ldr </span><span class="hljs-built_in">r1</span>, <span class="hljs-number">=0xffff</span>

  <span class="hljs-comment">@ your code goes here</span>

<span class="hljs-comment">@ when it's all done, spin in an infinite loop</span>
<span class="hljs-symbol">loop</span>:
  <span class="hljs-keyword">nop
</span>  <span class="hljs-keyword">b </span>loop
</code></pre>
<table class="conversion-widget">
<tbody>
<tr>
<td class="basetype">Decimal</td>
<td><input id="dec_val" type="text" value="0"></td>
</tr>
<tr>
<td class="basetype">Hex</td>
<td><input id="hex_val" type="text" value="0x 0000 0000"></td>
</tr>
<tr>
<td class="basetype">Binary</td>
<td><input id="bin_val" type="text" value="0b 0000 0000 0000 0000 0000 0000 0000 0000"></td>
</tr>
</tbody>
</table>
<div class="push-box">
Using&nbsp;<em>only</em>&nbsp;the instructions in the&nbsp;<strong>Logic</strong>&nbsp;and&nbsp;<strong>Shift/Rotate</strong>&nbsp;subsections of the cheat sheet (but as many registers as you need) write a program which puts&nbsp;<em>all</em>&nbsp;of the following values into the listed registers. Use the cheat sheet and the converter widget to help you out—draw “bit pattern” pictures on a piece of paper if it helps.

<ol>
<li><code>0xcafeffff</code>&nbsp;into&nbsp;<code>r3</code></li>
<li><code>0xcafe</code>&nbsp;into&nbsp;<code>r4</code></li>
<li><code>0xcaff0000</code>&nbsp;into&nbsp;<code>r5</code></li>
<li><code>0xc0fe0000</code>&nbsp;into&nbsp;<code>r6</code></li>
</ol>
</div>
These shouldn’t require heaps of code—just a couple of instructions for each. Remember the&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/labs/02-first-machine-code/">stuff you’ve</a>&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/labs/03-maths-to-machine-code/">done in</a>&nbsp;previous labs.

<p class="think-box">Did you need&nbsp;<em>both</em>&nbsp;of the “starting” values (e.g.&nbsp;<code>0xcafe0000</code>&nbsp;and&nbsp;<code>0xffff</code>) or could you have got the job done with only some of them? Which ones are essential?

<p class="extension-box">Can you do each task with only one instruction each?

<h2 id="using-labels">Exercise 1: using labels, ldr, and str</h2>
<h3 id="labels-and-loading-arbitrary-numbers-into-registers">Labels and loading arbitrary numbers into registers</h3>
<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/v_media/slides-pdf/COPE-02_Hardware-Software_Interface.01.pdf#page=24">Labels (Page 24)</a>&nbsp;are the symbols in your source code followed by a colon (<code>:</code>), e.g.&nbsp;<code>main:</code>. You’ve probably already got an intuitive feel for how they work: you put them in your code wherever you like, and when you want to branch to that part of the program you put the label in as the “destination” part of the branch instruction. Here’s an example:

<pre><code class="language-ARM hljs"><span class="hljs-symbol">loop</span>:
  <span class="hljs-comment">@ do stuff</span>

  <span class="hljs-keyword">b </span>loop <span class="hljs-comment">@ branch back to the "loop" label</span>
</code></pre>
In the&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/labs/03-maths-to-machine-code/">week 3 lab</a>&nbsp;you even used conditional branches to only branch under certain conditions (i.e., if certain flags were set). And we covered this in the&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/v_media/slides-pdf/COPE-02_Hardware-Software_Interface.01.pdf">week 4 lectures</a>&nbsp;as well—including how to turn “mathematical” conditional expressions (e.g.&nbsp;<code>x &gt;= -45</code>) into sequences of assembly instructions.

But what are labels, really? Add this code to your program (under the&nbsp;<code>main</code>&nbsp;label):

<pre><code class="language-ARM hljs"><span class="hljs-keyword">ldr </span><span class="hljs-built_in">r0</span>, <span class="hljs-symbol">=main</span>
</code></pre>
After you step through this line, what’s in&nbsp;<code>r0</code>? You might be wondering what the&nbsp;<code>=</code>&nbsp;sign is doing in your program. Remember from your week 2 lab that instructions are stored in memory with various encodings (some are 16-bit, some are 32-bit) and that when you use an&nbsp;<em>immediate value</em>&nbsp;constant (e.g.&nbsp;<code>42</code>) in an instruction which supports it then the bit pattern for&nbsp;<code>42</code>&nbsp;(which is&nbsp;<code>0b101010</code>) is stored&nbsp;<em>inside</em>&nbsp;that instruction.

This means that if you need to include a constant which is 32 bits long (e.g.&nbsp;<code>0xABCD1234</code>) then you can’t fit it in the instruction. You may have run into this problem already—the error message will be something like

<pre><code class="language-text">Error: invalid constant (ffffffffabcd1234) after fixup
</code></pre>
and what it means is that the constant value you’re using is too big (too many bits) for the instruction you’re trying to fit it inside.

<div class="extension-box">
If you’re interested in how exactly the ARM instruction set deals with this problem, and which constants&nbsp;<em>can</em>&nbsp;be stored inside a 32-bit instruction, then&nbsp;<a class="acton-tabs-link-processed" href="https://alisdair.mcdiarmid.org/arm-immediate-value-encoding/">here’s</a>&nbsp;an interesting blog post. Recall we use the Thumb-2 instruction set, so it’s not exactly the same on the discoboard (see section A5.3.2 in the reference manual for how they work on the discoboard).

Instead, you can play with the following widget to see how our board encodes a shift. The top input is the 12-bit encoded value. The second input is the 32-bit expanded output. Below this, the longer table is the binary representation of the output. An orange colour represents one of the 4 “special” shifts, while blue means it is a regular shifted byte. Similarly, the shorter table shows the parts of the encoded input, with the shift in purple and the data in green. Note how bit 7 of the encoded input is conditionally part of the shift or data, depending on bits 10 and 11. Each bit in the binary table can also be toggled by clicking it.

</div>
<div class="barrel-shifter-widget">
<div class="barrel-shifter-input"><input id="shifter_input" type="text" value="0b 0000 0000 0000"></div>
<div class="barrel-shifter-output"><input id="shifter_output" type="text" value="0b 0000 0000 0000 0000 0000 0000 0000 0000"><select id="shift_output_kind" title="Change output base" name="shift_output_kind" onchange="updateShifterOutputFormat()"><option value="bin">Bin</option><option value="dec_signed">Dec (s)</option><option value="dec_unsigned">Dec (u)</option><option value="hex">Hex</option></select><button title="Rotate output left">ROL</button><button title="Rotate output right">ROR</button><button title="Add 1 to output">+</button><button title="Subtract 1 from output">–</button></div>
<div class="barrel-shifter-details">
<div id="barrel-shifter-decoded">
313029282726252423222120191817161514131211109876543210

<table>
<thead></thead>
<tbody>
<tr>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-empty">0</td>
<td class="barrel-decode-special">0</td>
<td class="barrel-decode-special">0</td>
<td class="barrel-decode-special">0</td>
<td class="barrel-decode-special">0</td>
<td class="barrel-decode-special">0</td>
<td class="barrel-decode-special">0</td>
<td class="barrel-decode-special">0</td>
<td class="barrel-decode-special">0</td>
</tr>
</tbody>
</table>
</div>
<div id="barrel-shifter-encoded">
11109876543210

<table>
<thead></thead>
<tbody>
<tr>
<td class="barrel-encode-shift">0</td>
<td class="barrel-encode-shift">0</td>
<td class="barrel-encode-shift">0</td>
<td class="barrel-encode-shift">0</td>
<td class="barrel-encode-data">0</td>
<td class="barrel-encode-data">0</td>
<td class="barrel-encode-data">0</td>
<td class="barrel-encode-data">0</td>
<td class="barrel-encode-data">0</td>
<td class="barrel-encode-data">0</td>
<td class="barrel-encode-data">0</td>
<td class="barrel-encode-data">0</td>
</tr>
</tbody>
</table>
</div>
<div id="barrel-shifter-error-msg"></div>
</div>
</div>
Because this is a bit of a pain, the assembler provides a special syntax for storing larger values in registers. It’s based around the&nbsp;<code>ldr</code>&nbsp;(load register) instruction, and if you prefix the constant with an&nbsp;<code>=</code>&nbsp;sign then the assembler will generate the code to load the full value into the register, as we discussed in the&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/v_media/slides-pdf/COPE-02_Hardware-Software_Interface.01.pdf">week 4 lectures</a>.

<div class="extension-box">
Have a look at these two lines of assembly code:

<pre><code class="language-ARM hljs"><span class="hljs-keyword">mov </span><span class="hljs-built_in">r0</span>, <span class="hljs-number">0xFFF</span>
<span class="hljs-keyword">ldr </span><span class="hljs-built_in">r0</span>, <span class="hljs-number">=0xFFF</span>
</code></pre>
will they result in the same assembly instructions when uploaded &amp; running on your discoboard? How might you check?&nbsp;<em>Hint:</em>&nbsp;the disassembler is your friend 😊.

Can you think of any&nbsp;<em>other</em>&nbsp;lines of assembly code (apart from the two above) which will be assembled into the same machine instruction(s)?

</div>
So how does this relate to the&nbsp;<code>ldr r0, =main</code>&nbsp;instruction above? Well, the answer is that the labels in your program are just values—they’re the addresses (in your board’s memory space) of the instruction which occurs after them in the program. After the linker figures out exactly which address each label points to, it “replaces” them in the program, so that

<pre><code class="language-ARM hljs"><span class="hljs-keyword">ldr </span><span class="hljs-built_in">r0</span>, <span class="hljs-symbol">=main</span>
</code></pre>
becomes&nbsp;<em>something like</em>

<pre><code class="language-ARM hljs"><span class="hljs-keyword">ldr </span><span class="hljs-built_in">r0</span>, <span class="hljs-number">=0x80001c8</span>
</code></pre>
or whatever address the&nbsp;<code>main</code>&nbsp;label ends up pointing to (which will change every time your program changes).

And since&nbsp;<code>0x80001c4</code>&nbsp;(or whatever it is) is just a bit pattern in a register, you can do the usual arithmetic/logic stuff you can do with any values in registers:

<p class="push-box">Write a small program which calculates the size (in memory) of the&nbsp;<code>movs r3, 1</code>&nbsp;instruction and stores the result in&nbsp;<code>r0</code>.

<h2 id="load-twiddle-store">Exercise 2: the load-twiddle-store pattern</h2>
The&nbsp;<strong>load-twiddle-store</strong>&nbsp;pattern is a fundamental pattern in making your discoboard do useful work. The basic idea is this:

<ol>
<li>load some data from memory into a register</li>
<li>operate on (“twiddle”) the value in the register (e.g. with an&nbsp;<code>add</code>&nbsp;or&nbsp;<code>and</code>&nbsp;instruction)</li>
<li>store this new value from the register back into memory</li>
</ol>
<img data-recalc-dims="1" decoding="async" data-src="https://i0.wp.com/cs.anu.edu.au/courses/comp2300/assets/labs/lab-5/load-twiddle-store.jpg?w=980&amp;ssl=1" alt="load-twiddle-store" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==" class="lazyload">

If you’ve forgotten about “data” and “text” sections, you can review it in the&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/labs/05-functions/#sections">week 5 lab content</a>.

Let’s now make use of a data section to store some (spoilers) data, and attempt to load-twiddle-store.

<pre><code class="language-ARM hljs"><span class="hljs-symbol">main</span>:
  <span class="hljs-keyword">ldr </span><span class="hljs-built_in">r1</span>, <span class="hljs-symbol">=storage</span>
  <span class="hljs-comment">@ your code starts here</span>

<span class="hljs-symbol">.data</span>
<span class="hljs-symbol">storage</span>:
  <span class="hljs-meta">.word</span> <span class="hljs-number">2</span>, <span class="hljs-number">3</span>, <span class="hljs-number">0</span>, <span class="hljs-number">0</span> <span class="hljs-comment">@ don't change this line</span>
</code></pre>
<p class="push-box">Starting with the code above, use the&nbsp;<strong>load-twiddle-store</strong>&nbsp;pattern to change the first four data words to&nbsp;<code>2</code>&nbsp;<code>3</code>&nbsp;<code>0</code>&nbsp;<code>1</code>&nbsp;instead of&nbsp;<code>2</code>&nbsp;<code>3</code>&nbsp;<code>0</code>&nbsp;<code>0</code>. Hint: first load the&nbsp;<code>storage</code>&nbsp;label using the&nbsp;<code>=</code>&nbsp;instruction, then remember that you can&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/lectures/week-4/#load-and-store-with-offset">load and store with an offset</a>&nbsp;from this base address (check the cheat sheet). You’ll probably also want to use the memory browser view (like you did&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/labs/02-first-machine-code/#reverse-engineering">in week 2</a>) to watch the values change in memory.

<h2 id="exercise-2">Exercise 3: hello, LED!</h2>
So what does all that stuff have to do with blinking the LEDs? Well, the answer is that there’s a section of the discoboard’s&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/v_media/slides-pdf/COPE-02_Hardware-Software_Interface.01.pdf#page=23">address space (Page 23)</a>&nbsp;(<code>0x40000000</code>&nbsp;to&nbsp;<code>0x5FFFFFFF</code>) which is mapped to peripherals (as shown in the picture above). To interact with the LEDs, LCD, microphone etc. on the board you need to talk to the hardware by reading and writing to special memory locations in this memory range. To figure out exactly which addresses are mapped to which peripherals, you need to look at the discoboard&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/v_media/manuals/stm32-L476G-discovery-reference-manual.pdf">reference manual</a>

<img data-recalc-dims="1" decoding="async" data-src="https://i0.wp.com/cs.anu.edu.au/courses/comp2300/assets/labs/lab-5/discoboard-leds.png?w=980&amp;ssl=1" alt="discoboard with LEDs lit up" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==" class="lazyload">

One type of peripheral is a&nbsp;<a class="acton-tabs-link-processed" href="https://en.wikipedia.org/wiki/General-purpose_input/output">General Purpose Input/Output</a>&nbsp;pin. You can see them on your discoboard as little gold-coloured spikes sticking up out of the top and bottom of the board. Your discoboard has lots of them, and you can wire them up to other devices to make more sophisticated devices.

This exercise is pretty long, so here are the steps you’ll go through to turn on the LED:

<ol>
<li>enable the clock for correct LED GPIO pin</li>
<li>set the pin to output mode</li>
<li>set a bit in the pin’s data register to turn the LED on</li>
</ol>
Don’t worry if you don’t understand some of those terms—the rest of this exercise will explain all the details.

Some of the ports on the discoboard are already connected to certain bits of hardware on the board. In the&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/v_media/manuals/stm32-L476G-discovery-user-manual.pdf">discoboard&nbsp;<strong>user</strong>&nbsp;manual</a>&nbsp;Section 7.5&nbsp;<em>User interface: LCD, joystick, LEDs</em>&nbsp;it says:

<blockquote>
<ul>
<li>LD4 user: the red LED is a user LED connected to the I/O PB2 of the STM32L476VGT6</li>
<li>LD5 user: the green LED is a user LED connected to the I/O PE8 of the STM32L476VGT6</li>
</ul>
</blockquote>
The first bullet point says that the red LED is connected to GPIO pin&nbsp;<strong>PB2</strong>. This means that it’s connected to&nbsp;<strong>pin 2</strong>&nbsp;of&nbsp;<strong>port B</strong>. Just a note that the&nbsp;<em>user</em>&nbsp;manual (short) is different from the&nbsp;<em>reference</em>&nbsp;manual (long &amp; detailed).

<p class="think-box">What port+pin do you think the green LED is connected to?

The GPIO pins are grouped into 8 ports (port A to port E) and each port has 16 pins (pin). It’s worth pointing out that the pin numbering starts at 0, so the first pin in port A is PA0.

<img data-recalc-dims="1" decoding="async" data-src="https://i0.wp.com/cs.anu.edu.au/courses/comp2300/assets/labs/lab-5/ports-and-pins.jpg?w=980&amp;ssl=1" alt="Ports and pins" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==" class="lazyload">

From the&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/v_media/manuals/stm32-L476G-discovery-reference-manual.pdf">reference manual</a>:

<blockquote>Each general-purpose I/O port has four 32-bit configuration registers (GPIOx_MODER, GPIOx_OTYPER, GPIOx_OSPEEDR and GPIOx_PUPDR), two 32-bit data registers (GPIOx_IDR and GPIOx_ODR) and a 32-bit set/reset register (GPIOx_BSRR).
</blockquote>
Don’t worry if this seems overwhelming, the main point is that each of these ports has a few dedicated configuration registers—some are used to turn it on, some are used to set it up, and some are used to receive data (read the voltage on the pin as 0 or 1) or send data out (set the voltage to high or low). When it says&nbsp;<code>GPIOx</code>, that means that there exists a version for all the ports, so the port A version would be called&nbsp;<code>GPIOA</code>, etc.

These are not like the CPU registers you’ve been using so far (e.g.&nbsp;<code>r0</code>&nbsp;or&nbsp;<code>r5</code>). Instead, they’re mapped to certain parts of the address space (so they’re sometimes called memory-mapped registers). Read/write access to this register happens through load/store instructions to a specific memory address (as with pretty much everything in a&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/v_media/slides-pdf/COPE-02_Hardware-Software_Interface.01.pdf#page=27">load/store architecture (Page 27)</a>.

The register for turning on the clock (step 1) is in the&nbsp;<em>Reset and Clock Control (RCC)</em>&nbsp;section of the address space, which on your discoboard starts at memory address&nbsp;<code>0x40021000</code>. The specific register which controls the clock for GPIO ports is the&nbsp;<code>RCC_AHB2ENR</code>&nbsp;32-bit register, which lives at an offset of&nbsp;<code>0x4C</code>&nbsp;from the RCC base address and looks like this:

<img data-recalc-dims="1" decoding="async" data-src="https://i0.wp.com/cs.anu.edu.au/courses/comp2300/assets/labs/lab-5/AHB2ENR.png?w=980&amp;ssl=1" alt="RCC_AHB2ENR register" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==" class="lazyload">

As you can see, the clock for GPIO port B (where your red LED is) is controlled through bit 1 (i.e. the&nbsp;<em>second</em>&nbsp;bit from the right, because the rightmost bit is bit 0). You can have a look at Section 6.4.17 of the reference manual for all the gory details.

<p class="think-box">Why do we need to turn on a clock to even use the GPIO pins? Why aren’t they just permanently enabled to save us all the hassle? Hint: the discoboard is marketed as an “ultra-low-power microcontroller”. It’s designed to support being on battery power for long durations without recharging.

Note that in debug view you can conveniently see this information in the&nbsp;<strong>Peripherals</strong>&nbsp;pane:&nbsp;<img data-recalc-dims="1" decoding="async" data-src="https://i0.wp.com/cs.anu.edu.au/courses/comp2300/assets/labs/lab-5/peripheral-view.jpg?w=980&amp;ssl=1" alt="Peripheral View" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==" class="lazyload">

This is your chance to see the&nbsp;<strong>load-twiddle-store</strong>&nbsp;pattern from Exercise 1 in action. To turn on GPIO port B, you must:

<ol>
<li><strong>load</strong>: load the RCC base address into a register, then do an “offset”&nbsp;<code>ldr</code>&nbsp;with the&nbsp;<code>RCC_AHB2ENR</code>&nbsp;offset to read the current state of the&nbsp;<code>RCC_AHB2ENR</code>&nbsp;register into a CPU register</li>
<li><strong>twiddle</strong>: use bitwise operations to set the second-from-the-right&nbsp;<code>GPIOBEN</code>&nbsp;bit to 1 while leaving the other bits unchanged</li>
<li><strong>store</strong>: write the new&nbsp;<code>RCC_AHB2ENR</code>&nbsp;value back to the memory address you read it from earlier</li>
</ol>
<p class="info-box">When we talk about&nbsp;<strong>setting</strong>&nbsp;a bit, that means that it should be equal to&nbsp;<code>1</code>, and&nbsp;<strong>clearing</strong>&nbsp;a bit means it should be equal to&nbsp;<code>0</code>.

So what does the code to perform these load-twiddle-store steps look like?

<pre><code class="language-ARM hljs"><span class="hljs-comment">@ load r1 with the base address of RCC</span>
<span class="hljs-keyword">ldr </span><span class="hljs-built_in">r1</span>, <span class="hljs-number">=0x40021000</span>

<span class="hljs-comment">@ load r2 with the value of RCC_AHB2ENR</span>
<span class="hljs-comment">@ (note the 0x4C offset from the RCC base address)</span>
<span class="hljs-keyword">ldr </span><span class="hljs-built_in">r2</span>, [<span class="hljs-built_in">r1</span>, <span class="hljs-number">0x4C</span>]

<span class="hljs-comment">@ set bit 1 of this register by doing a logical or with 2</span>
<span class="hljs-comment">@ think: why does this work?</span>
<span class="hljs-keyword">orr </span><span class="hljs-built_in">r2</span>, <span class="hljs-number">0b10</span>

<span class="hljs-comment">@ store the modified result back in RCC_AHB2ENR</span>
<span class="hljs-keyword">str </span><span class="hljs-built_in">r2</span>, [<span class="hljs-built_in">r1</span>, <span class="hljs-number">0x4C</span>]
</code></pre>
<p class="think-box">Why is the&nbsp;<strong>load</strong>&nbsp;part of this process necessary? Why can’t you just store a&nbsp;<code>2</code>&nbsp;into the&nbsp;<code>RCC_AHB2ENR</code>&nbsp;register and be done with it?

You can paste the above code straight into your program. There are a couple more steps before you can actually turn the LED on, but they’re basically the same load-twiddle-store pattern, except with different addresses and “twiddles”.

Now it’s your turn: copy-paste a second copy of the code above as a starting point, but you’ll need different load/store addresses and different twiddles. To set pin 2 of GPIO port B to output mode, you need to set the&nbsp;<code>MODE2</code>&nbsp;bits (4 and 5) of the GPIO mode register&nbsp;<code>GPIOB_MODER</code>, which lives at an offset of&nbsp;<code>0x0</code>&nbsp;from the GPIO base address of&nbsp;<code>0x48000400</code>&nbsp;(see Section 7.4.1 of the manual for more info). Here’s what the&nbsp;<code>GPIOB_MODER</code>&nbsp;looks like:

<img data-recalc-dims="1" decoding="async" data-src="https://i0.wp.com/cs.anu.edu.au/courses/comp2300/assets/labs/lab-5/GPIOx_MODER.png?w=980&amp;ssl=1" alt="GPIOx_MODER register" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==" class="lazyload">

To configure pin 2 for output mode to power the LED, you need to ensure the mode bits for pin 2 (<code>MODE2</code>&nbsp;in the diagram) are&nbsp;<code>01</code>&nbsp;for output mode (i.e. clear bit 5, set bit 4).

<p class="extension-box">This output mode configuration for the mode register bits is sufficient for turning the LEDs on and off, but there are many more ways to configure the GPIO pins. If you’re interested, have a look in Section 7.4 of the manual.

Your PB2 pin is now configured and ready to roll. The only thing left to do is to actually send an “on” signal to it by setting a&nbsp;<code>1</code>&nbsp;into bit 2 (for pin 2) of the port B Output Data Register&nbsp;<code>GPIOB_ODR</code>, which lives at offset&nbsp;<code>0x14</code>&nbsp;from the GPIOB base address and looks like this:

<img data-recalc-dims="1" decoding="async" data-src="https://i0.wp.com/cs.anu.edu.au/courses/comp2300/assets/labs/lab-5/GPIOx_ODR.png?w=980&amp;ssl=1" alt="GPIOx_ODR register" src="data:image/gif;base64,R0lGODlhAQABAAAAACH5BAEKAAEALAAAAAABAAEAAAICTAEAOw==" class="lazyload">

<p class="push-box">Following the steps above, write a program which turns on the red LED on your discoboard, and push it up to your fork on GitLab.

<p class="info-box">The red and green LEDs are normally near the top left corner of the reset button. If you look closely, you can see the labels&nbsp;<code>LD4</code>&nbsp;and&nbsp;<code>LD5</code>&nbsp;on the board there. The LEDs above the LCD screen are not the ones we are working with.

<p class="talk-box">There are a few fiddly things which can go wrong here. If your LED isn’t coming on, talk with your neighbour/tutor about your program. Have you accidentally set the wrong bit (remember that the ports and bits are 0-indexed, so the rightmost bit is bit 0, not bit 1). Are you reading the existing register value correctly? Are you turning the bit on correctly? Are you writing it back to the right memory address? Step through the program with your partner to see what might be going wrong.

<p id="red-green-push" class="push-box">Once you can turn the red LED on, add code to turn the green one (PE8) as well. Commit &amp; push your red+green program up to GitLab.

<h2 id="exercise-4-functions-review">Exercise 4: functions review</h2>
<p class="info-box">Hey wow! You made it to&nbsp;<strong>Exercise 4</strong>&nbsp;which is about the&nbsp;<strong>halfway point</strong>&nbsp;for this lab! As we have both week 6 and week 7 for this lab, you can feel free to stop here and pick it up in week 7. Alternatively, if you’re preparing for week 6’s lab, make sure you understand everything up to this point. Of course if you&nbsp;<strong>want</strong>&nbsp;to keep going, I’m not going to stop you! Have fun! 😀

You should now feel a warm glow of satisfaction—let there be light! But you’ll also notice that a few of the steps you had to go through were pretty repetitive. For every step you just did, you were really doing one of two things:

<ul>
<li><strong>setting</strong>&nbsp;a specific bit at an offset from a base address,&nbsp;<em>or</em></li>
<li><strong>clearing</strong>&nbsp;a specifc bit at an offset from a base address</li>
</ul>
Wouldn’t it be good if we could “factor out” the common parts of those two tasks, so that the code is simpler and clearer? We can do that with&nbsp;<strong>functions</strong>&nbsp;(<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/labs/05-functions/">something you should remember from last week</a>). We’re going to take this quite slow, if you’re feeling confident–you can&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/labs/06-blinky/#function-parameters">skip to the second “push” box</a>&nbsp;and work from there.

<pre><code class="language-ARM hljs"><span class="hljs-symbol">set_bit_0x48000400_0x14_2</span>:
  <span class="hljs-comment">@ code to set bit 2 of word at offset 0x14 of 0x48000400</span>
  <span class="hljs-keyword">bx </span><span class="hljs-built_in">lr</span>
<span class="hljs-symbol">
main:</span>
  <span class="hljs-comment">@ ...</span>
  <span class="hljs-keyword">bl </span>set_bit_<span class="hljs-number">0x48000400</span>_<span class="hljs-number">0x14</span>_2
  <span class="hljs-keyword">b </span>main
</code></pre>
<p class="push-box">Update your&nbsp;<a class="acton-tabs-link-processed" href="https://cs.anu.edu.au/courses/comp2300/labs/06-blinky/#red-green-push">red+green</a>&nbsp;program by writing a few functions using the name pattern&nbsp;<code>set_bit_&lt;base&gt;_&lt;offset&gt;_&lt;index&gt;</code>&nbsp;and&nbsp;<code>clear_bit_&lt;base&gt;_&lt;offset&gt;_&lt;index&gt;</code>&nbsp;following the example above, so that your&nbsp;<code>main</code>&nbsp;function is just a series of&nbsp;<code>bl</code>&nbsp;instructions (and “spins” in an infinite loop at the end).

<h3 id="argumentsparameters">Arguments/parameters</h3>
You’ve now modularised your code (broken it up into smaller, re-usable parts), but it’s still pretty repetitive. There’s a lot of repeated code between the&nbsp;<code>set_bit_xxxx</code>&nbsp;functions.

The only difference between these repeated versions is the difference in inputs. Therefore we can pass&nbsp;<strong>arguments</strong>&nbsp;to functions to parameterise those functions, so that we just have one&nbsp;<code>set_bit</code>&nbsp;function that we call with different “inputs”.

As we learnt last week, we leave values in&nbsp;<code>r0</code>–<code>r3</code>&nbsp;before calling&nbsp;<code>bl</code>&nbsp;to act as “inputs” for our functions. Consider the following&nbsp;<code>sum_x_y</code>&nbsp;function:

<pre><code class="language-ARM hljs"><span class="hljs-symbol">main</span>:
  <span class="hljs-keyword">mov </span><span class="hljs-built_in">r0</span>, <span class="hljs-number">3</span>   <span class="hljs-comment">@ first argument, x</span>
  <span class="hljs-keyword">mov </span><span class="hljs-built_in">r1</span>, <span class="hljs-number">2</span>   <span class="hljs-comment">@ second argument, y</span>
  <span class="hljs-keyword">bl </span>sum_x_y  <span class="hljs-comment">@ call sum_x_y(3, 2)</span>
  <span class="hljs-comment">@ get result back in r0</span>

<span class="hljs-symbol">.type</span> sum_x_y, %<span class="hljs-meta">function</span>
<span class="hljs-comment">@ args:</span>
<span class="hljs-comment">@   r0: x</span>
<span class="hljs-comment">@   r1: y</span>
<span class="hljs-comment">@ result: r0</span>
<span class="hljs-symbol">sum_x_y</span>:
  <span class="hljs-keyword">add </span><span class="hljs-built_in">r0</span>, <span class="hljs-built_in">r1</span>
  <span class="hljs-keyword">bx </span><span class="hljs-built_in">lr</span>
<span class="hljs-symbol">.size</span> sum_x_y, .-sum_x_y
</code></pre>
The function adds the values in&nbsp;<code>r0</code>&nbsp;and&nbsp;<code>r1</code>&nbsp;and puts the result in&nbsp;<code>r0</code>. So the values in&nbsp;<code>r0</code>&nbsp;and&nbsp;<code>r1</code>&nbsp;are&nbsp;<strong>arguments</strong>&nbsp;(or&nbsp;<strong>parameters</strong>—same concept, different name). We can just leave the numbers we want to add in&nbsp;<code>r0</code>&nbsp;and&nbsp;<code>r1</code>, call the function&nbsp;<code>sum_x_y</code>, and expect the result to be in&nbsp;<code>r0</code>&nbsp;after it finishes.

Did you notice something “underhanded” going on between the caller (<code>main</code>) and the callee (<code>sum_x_y</code>)? There is an implicit contract/agreement as to

<ul>
<li>which registers hold the input arguments, and</li>
<li>which registers hold the result</li>
</ul>
This is called&nbsp;<strong>calling convention</strong>, a set of rules that all function calls are expected to adhere to. It is generally CPU architecture and programming language defined. There is more to calling convention, and it will be covered in lecture and in the next lab.

Note that there are some comments before the function about where the arguments are placed. It’s a good idea to document what these registers are expected to hold for readability and clarity’s sake.

<p id="function-parameters" class="push-box">Parameterise your&nbsp;<code>set_bit</code>&nbsp;and&nbsp;<code>clear_bit</code>&nbsp;functions so that they each take three arguments:&nbsp;<em>base address</em>,&nbsp;<em>offset</em>&nbsp;and&nbsp;<em>bit index</em>. Modify your&nbsp;<code>main</code>&nbsp;function so that turning the LED on and off is as easy as calling your&nbsp;<code>set_bit</code>&nbsp;or&nbsp;<code>clear_bit</code>&nbsp;functions with the right arguments. Commit &amp; push your newly-functional program to GitLab.

<p class="info-box">You might have noticed that we haven’t told you to store the&nbsp;<code>lr</code>&nbsp;register onto the stack–that’s cause you’re creating what are called “leaf” functions. These leaf functions&nbsp;<em>don’t</em>&nbsp;call other functions, so don’t need to worry about having&nbsp;<code>lr</code>&nbsp;overwritten.

<h2 id="exercise-5-blinky">Exercise 5: blinky</h2>
In this exercise you’ll add a simple loop into your program to blink one of the LEDs on and off. You can write a&nbsp;<code>delay</code>&nbsp;function to do this—do it now, and call it in-between your on and off instructions. Let the function take in an argument so that you can specify the number of steps to “delay” for.

There are a bunch of ways to do this, but one way is to

<ol>
<li>subtract 1 from an input register,</li>
<li><strong>if</strong>&nbsp;the value isn’t zero&nbsp;<strong>then</strong>&nbsp;goto step 1,&nbsp;<strong>else</strong>&nbsp;return back to the caller.</li>
</ol>
<p class="push-box">Modify your program so that after the initial setup code, there is a loop which turns the LED on, delays a little while, turns it back off, delays a little again, then branches back to the top of the loop.

Once you’ve done that, you should be able to blink the LEDs on your board to your heart’s content.

<h2 id="fizzblink">Exercise 6: FizzBlink</h2>
For the final exercise, you’ll make LED blinking more interesting by writing an ARM assembly version of the classic&nbsp;<a class="acton-tabs-link-processed" href="https://en.wikipedia.org/wiki/Fizz_buzz">FizzBuzz</a>&nbsp;childrens game (and a common&nbsp;<a class="acton-tabs-link-processed" href="https://blog.codinghorror.com/why-cant-programmers-program/">programming interview question</a>). The only difference is that instead of printing&nbsp;<code>"fizz"</code>&nbsp;or&nbsp;<code>"buzz"</code>&nbsp;to the screen (which you can’t do anyway, since we’re not running on the computer, you’re running on the discoboard) you’ll blink the LEDS on the board. So this new version is called&nbsp;<strong>FizzBlink</strong>, I guess.

Modify your program to:

<ol>
<li>count up from&nbsp;<code>0</code>&nbsp;to&nbsp;<code>100</code>&nbsp;in increments of&nbsp;<code>1</code></li>
<li>if the number is divisible by&nbsp;<code>3</code>, blink the&nbsp;<strong>red</strong>&nbsp;light for some period of time (use your delay function)</li>
<li>if the number is divisible by&nbsp;<code>5</code>, blink the&nbsp;<strong>green</strong>&nbsp;light for some period of time</li>
<li>if the number is divisible by both&nbsp;<code>3</code>&nbsp;<em>and</em>&nbsp;<code>5</code>, blink&nbsp;<strong>both</strong>&nbsp;lights</li>
</ol>

---
keywords: fastai
title: Parallel Computing Hacks
toc: true
categories: []
nb_path: _notebooks/2023-04-02-Parallel-Computing-Hacks.ipynb
layout: notebook
---

<!--
#################################################
### THIS FILE WAS AUTOGENERATED! DO NOT EDIT! ###
#################################################
# file to edit: _notebooks/2023-04-02-Parallel-Computing-Hacks.ipynb
-->

<div class="container" id="notebook-container">
        
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="AP-Classroom">AP Classroom<a class="anchor-link" href="#AP-Classroom"> </a></h3><blockquote><p>AP Classroom. Provide answers and thoughts on theoritical question form college board Video in section 4.3.  They start at about the 9 minute mark.</p>
</blockquote>
<h3 id="Example-1">Example 1<a class="anchor-link" href="#Example-1"> </a></h3><p>A particular computer has two identical processors which can run in parallel. Each Process must be executed on a single processor and each processor can only run one process at a time.</p>
<p>The table below lists the amount of time it takes to execute each of the processes on a single computer. None of the processes are dependent on any of the others.</p>
<p>What is the minimum amount of time to execute all three processes when the two processors are run in parallel?</p>
<table>
<thead><tr>
<th>Process</th>
<th>Execution Time on Either Processor</th>
</tr>
</thead>
<tbody>
<tr>
<td>X</td>
<td>50 seconds</td>
</tr>
<tr>
<td>Y</td>
<td>10 seconds</td>
</tr>
<tr>
<td>Z</td>
<td>30 seconds</td>
</tr>
</tbody>
</table>
<h4 id="Answer-1">Answer 1<a class="anchor-link" href="#Answer-1"> </a></h4><p>50 seconds</p>
<p>If we run the processes sequentially on a single processor, it will take a total of 50 + 10 + 30 = 90 seconds. However, we have two identical processors available, so we can run two processes in parallel. The bottleneck process will be the one with the longest execution time, which is process X with 50 seconds. The other two processes can be completed in the remaining time it takes to complete process X. So, we can run processes Y and Z simultaneously on the two processors, which will take a total of 30 seconds (since Z takes 30 seconds to execute). Once process Z is complete, we can use one processor to complete process X, which will take another 20 seconds. Therefore, the total time required to complete all three processes using both processors is 20 + 30 = 50 seconds. Thus, the minimum amount of time required to execute all three processes when the two processors are run in parallel is 50 seconds.</p>
<h3 id="Example-2">Example 2<a class="anchor-link" href="#Example-2"> </a></h3><p>A computer has two duplicate processors that are able to run in parallel. The table below shows the amount of time it takes each processor to execute each of two processes. Neither process is dependent on the other.</p>
<table>
<thead><tr>
<th>Process</th>
<th>Execution Time on Either Processor</th>
</tr>
</thead>
<tbody>
<tr>
<td>A</td>
<td>25 seconds</td>
</tr>
<tr>
<td>B</td>
<td>45 seconds</td>
</tr>
</tbody>
</table>
<p>What is the difference in execution time between running the two processes in parallel in place of running them one after the other on a single processor?</p>
<h4 id="Answer-2">Answer 2<a class="anchor-link" href="#Answer-2"> </a></h4><p>If the two processors are run in parallel, then process A and process B can be executed simultaneously on each processor. The total execution time will then be equal to the time required to complete the longest running process. So, in this case, the total execution time will be equal to the maximum of the execution time for process A and process B on either processor, which is:max(25 seconds, 45 seconds) = 45 seconds
Therefore, the difference in execution time between running the two processes in parallel and running them one after the other on a single processor is:</p>
<p>45 seconds - (25 seconds + 45 seconds) = 45 seconds - 70 seconds = -25 seconds</p>
<p>This negative result indicates that running the two processes in parallel is faster than running them one after the other on a single processor. The parallel execution would take 45 seconds to complete, while running them sequentially on a single processor would take 70 seconds.</p>
<h3 id="Data-Structures.--Build-a-List-Comprehension-example">Data Structures.  Build a List Comprehension example<a class="anchor-link" href="#Data-Structures.--Build-a-List-Comprehension-example"> </a></h3>
</div>
</div>
</div>
    {% raw %}
    
<div class="cell border-box-sizing code_cell rendered">
<div class="input">

<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">original_list</span> <span class="o">=</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">,</span> <span class="mi">6</span><span class="p">,</span> <span class="mi">7</span><span class="p">,</span> <span class="mi">8</span><span class="p">,</span> <span class="mi">9</span><span class="p">,</span> <span class="mi">10</span><span class="p">]</span>
<span class="n">even_numbers</span> <span class="o">=</span> <span class="p">[</span><span class="n">x</span> <span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="n">original_list</span> <span class="k">if</span> <span class="n">x</span> <span class="o">%</span> <span class="mi">2</span> <span class="o">==</span> <span class="mi">0</span><span class="p">]</span>
<span class="nb">print</span><span class="p">(</span><span class="n">even_numbers</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">

<div class="output_area">

<div class="output_subarea output_stream output_stdout output_text">
<pre>[2, 4, 6, 8, 10]
</pre>
</div>
</div>

</div>
</div>

</div>
    {% endraw %}

</div>
 

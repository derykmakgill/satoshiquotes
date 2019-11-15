---
layout: default
---


<h3>Contents</h3>

<ul>
<li><a href="#doctype">Declare a doctype</a></li>
<li><a href="#box-model-math">Box model math</a></li>
<li><a href="#rems-mobile-safari">Rem units and Mobile Safari</a></li>
<li><a href="#floats-first">Floats first</a></li>
<li><a href="#floats-clearing">Floats and clearing</a></li>
<li><a href="#floats-computed-height">Floats and computed height</a></li>
<li><a href="#floats-block-level">Floated are block level</a></li>
<li><a href="#vertical-margins-collapse">Vertical margins often collapse</a></li>
<li><a href="#styling-table-rows">Styling table rows</a></li>
<li><a href="#buttons-firefox">Firefox and <code>&lt;input&gt;</code> buttons</a></li>
<li><a href="#buttons-firefox-outline">Firefox inner outline on buttons</a></li>
<li><a href="#buttons-type">Always set a <code>type</code> on <code>&lt;button&gt;</code>s</a></li>
<li><a href="#ie-selector-limit">Internet Explorer&#39;s selector limit</a></li>
<li><a href="#position-explained">Position explained</a></li>
<li><a href="#position-width">Position and width</a></li>
<li><a href="#position-transforms">Fixed position and transforms</a></li>
</ul>

<p><a name="doctype"></a></p>

<h3>A pre-release draft</h3>

<p>The earliest draft of the white paper was called 'e-Cash' not 'Bitcoin.'</p>
<div class="highlight">
<p>
You can download a pre-release draft at
http://www.upload.ae/file/6157/ecash-pdf.html  Feel free to forward it to
  anyone else you think would be interested.</p>
<p>Title: Electronic Cash Without a Trusted Third Party</p></div>
<p><a href="http://quirks.spec.whatwg.org">Skipping the doctype can cause issues</a> with malformed tables, inputs, and more as the page will be rendered in quirks mode.</p>

<p><a name="box-model-math"></a></p>

<h3>Box model math</h3>

<p>Elements that have a set <code>width</code> become <em>wider</em> when they have <code>padding</code> and/or <code>border-width</code>. To avoid these problems, make use of the now common <a href="http://www.paulirish.com/2012/box-sizing-border-box-ftw/"><code>box-sizing: border-box;</code> reset</a>.</p>

<p><a name="rems-mobile-safari"></a></p>

<h3>Rem units and Mobile Safari</h3>

<p>While Mobile Safari supports the use of <code>rem</code>s in all property values, it seems to shit the bed when <code>rem</code>s are used in dimensional media queries and infinitely flashes the page&#39;s text in different sizes.</p>

<p>For now, use <code>em</code>s in place of <code>rem</code>s.</p>
<div class="highlight"><pre><code class="language-css" data-lang="css"><span class="nt">html</span> <span class="p">{</span>
  <span class="nl">font-size</span><span class="p">:</span> <span class="m">16px</span><span class="p">;</span>
<span class="p">}</span>

<span class="c">/* Causes flashing bug in Mobile Safari */</span>
<span class="k">@media</span> <span class="p">(</span><span class="n">min-width</span><span class="p">:</span> <span class="m">40rem</span><span class="p">)</span> <span class="p">{</span>
  <span class="nt">html</span> <span class="p">{</span>
    <span class="nl">font-size</span><span class="p">:</span> <span class="m">20px</span><span class="p">;</span>
  <span class="p">}</span>
<span class="p">}</span>

<span class="c">/* Works great in Mobile Safari */</span>
<span class="k">@media</span> <span class="p">(</span><span class="n">min-width</span><span class="p">:</span> <span class="m">40em</span><span class="p">)</span> <span class="p">{</span>
  <span class="nt">html</span> <span class="p">{</span>
    <span class="nl">font-size</span><span class="p">:</span> <span class="m">20px</span><span class="p">;</span>
  <span class="p">}</span>
<span class="p">}</span>
</code></pre></div>
<p><strong>Help!</strong> <em>If you have a link to an Apple or WebKit bug report for this, I&#39;d love to include it. I&#39;m unsure where to report this as it only applies to Mobile, and not Desktop, Safari.</em></p>

<p><a name="floats-first"></a></p>

<h3>Floats first</h3>

<p>Floated elements should always come first in the document order. Floated elements require something to wrap around, otherwise they can cause a step down effect, instead appearing below the content.</p>
<div class="highlight"><pre><code class="language-html" data-lang="html"><span class="nt">&lt;div</span> <span class="na">class=</span><span class="s">"parent"</span><span class="nt">&gt;</span>
  <span class="nt">&lt;div</span> <span class="na">class=</span><span class="s">"float"</span><span class="nt">&gt;</span>Float<span class="nt">&lt;/div&gt;</span>
  <span class="nt">&lt;div</span> <span class="na">class=</span><span class="s">"content"</span><span class="nt">&gt;</span>
    <span class="c">&lt;!-- ... --&gt;</span>
  <span class="nt">&lt;/div&gt;</span>
<span class="nt">&lt;/div&gt;</span>
</code></pre></div>
<p><a name="floats-clearing"></a></p>

<h3>Floats and clearing</h3>

<p>If you float it, you <em>probably</em> need to clear it. Any content that follows an element with a <code>float</code> will wrap around that element until cleared. To clear floats, use one of the following techniques.</p>

<p>Use <a href="http://nicolasgallagher.com/micro-clearfix-hack/">the micro clearfix</a> to clear your floats with a separate class.</p>
<div class="highlight"><pre><code class="language-css" data-lang="css"><span class="nc">.clearfix</span><span class="nd">:before</span><span class="o">,</span>
<span class="nc">.clearfix</span><span class="nd">:after</span> <span class="p">{</span>
  <span class="nl">display</span><span class="p">:</span> <span class="n">table</span><span class="p">;</span>
  <span class="nl">content</span><span class="p">:</span> <span class="s1">""</span><span class="p">;</span>
<span class="p">}</span>
<span class="nc">.clearfix</span><span class="nd">:after</span> <span class="p">{</span>
  <span class="nl">clear</span><span class="p">:</span> <span class="nb">both</span><span class="p">;</span>
<span class="p">}</span>
</code></pre></div>
<p>Alternatively, specify <code>overflow</code>, with <code>auto</code> or <code>hidden</code>, on the parent.</p>
<div class="highlight"><pre><code class="language-css" data-lang="css"><span class="nc">.parent</span> <span class="p">{</span>
  <span class="nl">overflow</span><span class="p">:</span> <span class="nb">auto</span><span class="p">;</span> <span class="c">/* clearfix */</span>
<span class="p">}</span>
<span class="nc">.other-parent</span> <span class="p">{</span>
  <span class="nl">overflow</span><span class="p">:</span> <span class="nb">hidden</span><span class="p">;</span> <span class="c">/* clearfix */</span>
<span class="p">}</span>
</code></pre></div>
<p>Be aware that <code>overflow</code> can cause other unintended side effects, typically around positioned elements within the parent.</p>

<p><strong>Pro-Tip!</strong> <em>Keep your future self and your coworkers happy by including a comment like `/</em> clearfix <em>/` when clearing floats as the property can be used for other reasons.</em></p>

<p><a name="floats-computed-height"></a></p>

<h3>Floats and computed height</h3>

<p>A parent element that has only floated content will have a computed <code>height: 0;</code>. Add a clearfix to the parent to force browsers to compute a height.</p>

<p><a name="floats-block-level"></a></p>

<h3>Floated elements are block level</h3>

<p>Elements with a <code>float</code> will automatically become <code>display: block;</code>. Do not set both as there is no need and the <code>float</code> will override your <code>display</code>.</p>
<div class="highlight"><pre><code class="language-css" data-lang="css"><span class="nc">.element</span> <span class="p">{</span>
  <span class="nl">float</span><span class="p">:</span> <span class="nb">left</span><span class="p">;</span>
  <span class="nl">display</span><span class="p">:</span> <span class="nb">block</span><span class="p">;</span> <span class="c">/* Not necessary */</span>
<span class="p">}</span>
</code></pre></div>
<p><strong>Fun fact:</strong> <em>Years ago, we had to set <code>display: inline;</code> for most floats to work properly in IE6 to avoid the <a href="http://www.positioniseverything.net/explorer/doubled-margin.html">double margin bug</a>. However, those days have long passed.</em></p>

<p><a name="vertical-margins-collapse"></a></p>

<h3>Vertically adjacent margins collapse</h3>

<p>Top and bottom margins on adjacent elements (one after the other) can and will collapse in many situations, but never for floated or absolutely positioned elements. <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/margin_collapsing">Read this MDN article</a> or the CSS2 spec&#39;s <a href="http://www.w3.org/TR/CSS2/box.html#collapsing-margins">collapsing margin section</a> to find out more.</p>

<p>Horizontally adjacent margins will <strong>never collapse</strong>.</p>

<p><a name="styling-table-rows"></a></p>

<h3>Styling table rows</h3>

<p>Table rows, <code>&lt;tr&gt;</code>s, do not receive <code>border</code>s unless you set <code>border-collapse: collapse;</code> on the parent <code>&lt;table&gt;</code>. Moreover, if the <code>&lt;tr&gt;</code> and children <code>&lt;td&gt;</code>s or <code>&lt;th&gt;</code>s have the <em>same</em> <code>border-width</code>, the rows will not see their border applied. <a href="http://jsbin.com/yabek/2/">See this JS Bin link for an example.</a></p>

<p><a name="buttons-firefox"></a></p>

<h3>Firefox and <code>&lt;input&gt;</code> buttons</h3>

<p>For reasons unknown, Firefox applies a <code>line-height</code> to submit and button <code>&lt;input&gt;</code>s that cannot be overridden with custom CSS. You have two options in dealing with this:</p>

<ol>
<li>Stick to <code>&lt;button&gt;</code> elements</li>
<li>Don&#39;t use <code>line-height</code> on your buttons</li>
</ol>

<p>Should you go with the first route (and I recommend this one anyway because <code>&lt;button&gt;</code>s are great), here&#39;s what you need to know:</p>
<div class="highlight"><pre><code class="language-html" data-lang="html"><span class="c">&lt;!-- Not so good --&gt;</span>
<span class="nt">&lt;input</span> <span class="na">type=</span><span class="s">"submit"</span> <span class="na">value=</span><span class="s">"Save changes"</span><span class="nt">&gt;</span>
<span class="nt">&lt;input</span> <span class="na">type=</span><span class="s">"button"</span> <span class="na">value=</span><span class="s">"Cancel"</span><span class="nt">&gt;</span>

<span class="c">&lt;!-- Super good everywhere --&gt;</span>
<span class="nt">&lt;button</span> <span class="na">type=</span><span class="s">"submit"</span><span class="nt">&gt;</span>Save changes<span class="nt">&lt;/button&gt;</span>
<span class="nt">&lt;button</span> <span class="na">type=</span><span class="s">"button"</span><span class="nt">&gt;</span>Cancel<span class="nt">&lt;/button&gt;</span>
</code></pre></div>
<p>Should you wish to go the second route, just don&#39;t set a <code>line-height</code> and use <em>only</em> <code>padding</code> to vertically align button text. <a href="http://jsbin.com/yabek/4/">View this JS Bin example</a> in Firefox to see the original problem and the workaround.</p>

<p><strong>Good news!</strong> <em>It looks like <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=697451#c43">a fix for this</a> might be coming in Firefox 30. That&#39;s good news for our future selves, but be aware this doesn&#39;t fix older versions.</em></p>

<p><a name="buttons-firefox-outline"></a></p>

<h3>Firefox inner outline on buttons</h3>

<p>Firefox <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button#Notes">adds an inner outline</a> to buttons (<code>&lt;input&gt;</code>s and <code>&lt;button&gt;</code>s) on <code>:focus</code>. Apparently it&#39;s for accessibility, but its placement seems rather odd. Use this CSS to override it:</p>
<div class="highlight"><pre><code class="language-css" data-lang="css"><span class="nt">input</span><span class="nd">::-moz-focus-inner</span><span class="o">,</span>
<span class="nt">button</span><span class="nd">::-moz-focus-inner</span> <span class="p">{</span>
  <span class="nl">padding</span><span class="p">:</span> <span class="m">0</span><span class="p">;</span>
  <span class="nl">border</span><span class="p">:</span> <span class="m">0</span><span class="p">;</span>
<span class="p">}</span>
</code></pre></div>
<p>You can see this fix in action in the same <a href="http://jsbin.com/yabek/4/">JS Bin example</a> mentioned in the previous section.</p>

<p><strong>Pro-Tip!</strong> <em>Be sure to include some focus state on buttons, links, and inputs. Providing an affordance for accessibility is paramount, both for pro users who tab through content and those with vision impairments.</em></p>

<p><a name="buttons-type"></a></p>

<h3>Always set a <code>type</code> on <code>&lt;button&gt;</code>s</h3>

<p>The default value is <code>submit</code>, meaning any button in a form can submit the form. Use <code>type=&quot;button&quot;</code> for anything that doesn&#39;t submit the form and <code>type=&quot;submit&quot;</code> for those that do.</p>
<div class="highlight"><pre><code class="language-html" data-lang="html"><span class="nt">&lt;button</span> <span class="na">type=</span><span class="s">"submit"</span><span class="nt">&gt;</span>Save changes<span class="nt">&lt;/button&gt;</span>
<span class="nt">&lt;button</span> <span class="na">type=</span><span class="s">"button"</span><span class="nt">&gt;</span>Cancel<span class="nt">&lt;/button&gt;</span>
</code></pre></div>
<p>For actions that require a <code>&lt;button&gt;</code> and are not in a form, use the <code>type=&quot;button&quot;</code>.</p>
<div class="highlight"><pre><code class="language-html" data-lang="html"><span class="nt">&lt;button</span> <span class="na">class=</span><span class="s">"dismiss"</span> <span class="na">type=</span><span class="s">"button"</span><span class="nt">&gt;</span>x<span class="nt">&lt;/button&gt;</span>
</code></pre></div>
<p><strong>Fun fact:</strong> <em>Apparently IE7 doesn&#39;t properly support the <code>value</code> attribute on <code>&lt;button&gt;</code>s. Instead of reading the attribute&#39;s content, it pulls from the innerHTML (the content between the opening and closing <code>&lt;button&gt;</code> tags). However, I don&#39;t see this as a huge concern for two reasons: IE7 usage is way down, and it seems rather uncommon to set both a <code>value</code> and the innerHTML on <code>&lt;button&gt;</code>s.</em></p>

<p><a name="ie-selector-limit"></a></p>

<h3>Internet Explorer&#39;s selector limit</h3>

<p>Internet Explorer 9 and below have a max of 4,096 selectors per stylesheet. There is also a limit of 31 combined stylesheets and <code>&lt;style&gt;&lt;/style&gt;</code> includes per page. Anything after this limit is ignored by the browser. Either split your CSS up, or start refactoring. I&#39;d suggest the latter.</p>

<p>As a helpful side note, here&#39;s how browsers count selectors:</p>
<div class="highlight"><pre><code class="language-css" data-lang="css"><span class="c">/* One selector */</span>
<span class="nc">.element</span> <span class="p">{</span> <span class="p">}</span>

<span class="c">/* Two more selectors */</span>
<span class="nc">.element</span><span class="o">,</span>
<span class="nc">.other-element</span> <span class="p">{</span> <span class="p">}</span>

<span class="c">/* Three more selectors */</span>
<span class="nt">input</span><span class="o">[</span><span class="nt">type</span><span class="o">=</span><span class="s1">"text"</span><span class="o">],</span>
<span class="nc">.form-control</span><span class="o">,</span>
<span class="nc">.form-group</span> <span class="o">&gt;</span> <span class="nt">input</span> <span class="p">{</span> <span class="p">}</span>
</code></pre></div>
<p><a name="position-explained"></a></p>

<h3>Position explained</h3>

<p>Elements with <code>position: fixed;</code> are placed relative to the browser viewport. Elements with <code>position: absolute;</code> are placed relative to their closest parent with a position other than <code>static</code> (e.g., <code>relative</code>, <code>absolute</code>, or <code>fixed</code>).</p>

<p><a name="position-width"></a></p>

<h3>Position and width</h3>

<p>Don&#39;t set <code>width: 100%;</code> on an element that has <code>position: [absolute|fixed];</code>, <code>left</code>, and <code>right</code>. The use of <code>width: 100%;</code> is the same as the combined use of <code>left: 0;</code> and <code>right: 0;</code>. Use one or the other, but not both.</p>

<p><a name="position-transforms"></a></p>

<h3>Fixed position and transforms</h3>

<p>Browsers break <code>position: fixed;</code> when an element&#39;s parent has a <code>transform</code> set. Using transforms creates a new containing block, effectively forcing the parent to have <code>position: relative;</code> and the fixed element to behave as <code>position: absolute;</code>.</p>

<p><a href="http://jsbin.com/yabek/1/">See the demo</a> and read <a href="http://meyerweb.com/eric/thoughts/2011/09/12/un-fixing-fixed-elements-with-css-transforms/">Eric Meyer&#39;s post on the matter</a>.</p>


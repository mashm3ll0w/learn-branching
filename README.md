<!DOCTYPE html>
<!-- saved from url=(0067)file:///home/bones/Desktop/cool-projects/markdownify-web/index.html -->
<html><head><meta http-equiv="Content-Type" content="text/html; charset=windows-1252">
      <title>Markdownify</title>
      <link href="file:///home/bones/Desktop/cool-projects/markdownify-web/css/bootstrap.min.css" rel="stylesheet">
      <link href="file:///home/bones/Desktop/cool-projects/markdownify-web/css/style.css" rel="stylesheet">
      <link rel="stylesheet" href="file:///home/bones/Desktop/cool-projects/markdownify-web/css/codemirror.css">
      <link rel="stylesheet" href="file:///home/bones/Desktop/cool-projects/markdownify-web/css/base16-dark.css">
      <link rel="stylesheet" href="file:///home/bones/Desktop/cool-projects/markdownify-web/css/font-awesome.min.css">
      <link rel="stylesheet" href="file:///home/bones/Desktop/cool-projects/markdownify-web/css/dialog.css">
      <!-- for Google -->
      <meta name="description" content="A minimalist markdown editor app">
      <meta name="keywords" content="markdown,editor,javascript">

      <meta name="author" content="Amit Merchant">
      <meta name="copyright" content="MIT">
      <meta name="application-name" content="Markdownify">

      <!-- for Facebook -->
      <meta property="og:title" content="Markdownify">
      <meta property="og:type" content="article">
      <meta property="og:image" content="https://raw.githubusercontent.com/amitmerchant1990/markdownify-web/master/img/markdownify.png">
      <meta property="og:url" content="http://www.amitmerchant.com/markdownify-web">
      <meta property="og:description" content="A minimalist markdown editor app">

      <!-- for Twitter -->
      <meta name="twitter:card" content="summary">
      <meta name="twitter:title" content="Markdownify">
      <meta name="twitter:description" content="A minimalist markdown editor app">
      <meta name="twitter:image" content="https://raw.githubusercontent.com/amitmerchant1990/markdownify-web/master/img/markdownify.png">
      <script async="" src="./README_files/analytics.js"></script><script>
        (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
        (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
        m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
        })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

        ga('create', 'UA-43339302-3', 'auto');
        ga('send', 'pageview');

      </script>
  </head>
  <body class="container-fluid">
      <div class="main-title">
        <span class="app-title">
          Markdownify
        </span>
        <span class="git-buttons">
          <!-- Place this tag where you want the button to render. -->
          <a href="https://github.com/amitmerchant1990/markdownify" class="btn btn-success" target="_blank">Try Desktop Version</a>
          <span></span>
          <span></span>
        </span>
      </div>
      <div class="optContainer">
        <div class="mode">
          <span class="toolContainer">
            <a id="angleToolBar" title="Toolbar" class="fa fa-angle-double-right" onclick="showToolBar();" style="cursor: pointer;text-decoration:none;"></a>
          </span>
          <span>
            <input type="radio" name="changeTheme" value="light" onclick="changeTheme(this);" title="Light Mode" checked="checked"> <label style="vertical-align: middle;" title="Light Mode"><b>Light</b></label>
            <input type="radio" name="changeTheme" value="dark" onclick="changeTheme(this);" title="Dark Mode"> <label style="vertical-align: middle;" title="Dark Mode"><b>Dark</b></label>
          </span>
        </div>
        <div class="pref" id="pref">
          <input type="radio" name="showPreference" value="html" onclick="clkPref(this);"> <label style="vertical-align: middle;"><b>HTML</b></label>
          <input type="radio" name="showPreference" value="preview" onclick="clkPref(this);" checked="checked"> <label style="vertical-align: middle;"><b>Preview</b></label>
        </div>
      </div>
      <div id="toolbarArea">
        <div style="padding-left:10px;">
          <a onclick="toggleFormat(&#39;bold&#39;);" title="Bold [Ctrl+B]" class="fa fa-bold editor-toolbar"></a>
          <a onclick="toggleFormat(&#39;italic&#39;);" title="Italic [Ctrl+I]" class="fa fa-italic editor-toolbar"></a>
          <a onclick="toggleHeadingSmaller();" title="Header [Ctrl+H]" class="fa fa-header editor-toolbar"></a>
          <a onclick="toggleFormat(&#39;strikethrough&#39;);" title="StrikeThrough [Ctrl+/]" class="fa fa-strikethrough editor-toolbar"></a>
          <i class="separator">|</i>
          <a onclick="toggleBlockquote();" title="Quote" class="fa fa-quote-left editor-toolbar"></a>
          <a onclick="toggleUnorderedList();" title="Unordered List" class="fa fa-list-ul editor-toolbar"></a>
          <a onclick="toggleOrderedList();" title="Ordered List" class="fa fa-list-ol editor-toolbar"></a>
          <i class="separator">|</i>
          <a onclick="drawLink();" title="Create Link [Ctrl+L]" class="fa fa-link editor-toolbar"></a>
          <a onclick="drawImage();" title="Insert Image [Ctrl+Alt+I]" class="fa fa-picture-o editor-toolbar"></a>
          <a onclick="drawTable();" title="Insert Table [Ctrl+Shift+T]" class="fa fa-table editor-toolbar"></a>
          <a onclick="drawHorizontalRule();" title="Insert Horizontal Rule" class="fa fa-minus editor-toolbar"></a>
          <i class="separator">|</i>
          <a onclick="toggleSidePanel();" title="Side-By-Side Panel Toggle" class="fa fa-columns editor-toolbar"></a>
          <a data-toggle="modal" data-target="#myModal" title="Markdown Help" class="fa fa-question-circle editor-toolbar"></a>
        </div>
      </div>
      <section class="row" id="editArea" style="padding-top: 63px;">
          <div class="col-md-6 full-height" style="box-shadow: -10px 13px 6px 10px rgba(0,0,0,0.4);" id="textPanel">
            <textarea id="plainText" placeholder="Write your Markdown here.." autofocus="" style="display: none;"></textarea><div class="CodeMirror CodeMirror-wrap cm-s-base16-dark CodeMirror-focused"><div style="overflow: hidden; position: relative; width: 3px; height: 0px; top: 488px; left: 445.859px;"><textarea autocorrect="off" autocapitalize="off" spellcheck="false" style="position: absolute; padding: 0px; width: 1000px; height: 1em; outline: none;" tabindex="0"></textarea></div><div class="CodeMirror-vscrollbar" cm-not-content="true" style="bottom: 0px;"><div style="min-width: 1px; height: 0px;"></div></div><div class="CodeMirror-hscrollbar" cm-not-content="true"><div style="height: 100%; min-height: 1px; width: 0px;"></div></div><div class="CodeMirror-scrollbar-filler" cm-not-content="true"></div><div class="CodeMirror-gutter-filler" cm-not-content="true"></div><div class="CodeMirror-scroll" tabindex="-1"><div class="CodeMirror-sizer" style="margin-left: 29px; margin-bottom: -12px; border-right-width: 18px; min-height: 514px; padding-right: 0px; padding-bottom: 0px;"><div style="position: relative; top: 0px;"><div class="CodeMirror-lines"><div style="position: relative; outline: none;"><div class="CodeMirror-measure"><pre>x</pre></div><div class="CodeMirror-measure"></div><div style="position: relative; z-index: 1;"></div><div class="CodeMirror-cursors" style=""><div class="CodeMirror-cursor" style="left: 416.859px; top: 484px; height: 22px;">&nbsp;</div></div><div class="CodeMirror-code" style=""><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">1</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span class="cm-header cm-header-1"># GIT BRANCHING </span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">2</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span cm-text="">&#8203;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">3</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span class="cm-header cm-header-2">## Learn Git Branching</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">4</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span cm-text="">&#8203;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">5</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;">Introduce git branching and the powerful, efficient and time saving features that branching enables one to perform.</span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">6</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span cm-text="">&#8203;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">7</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span class="cm-header cm-header-2">## How to use</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">8</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span class="cm-comment">```</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">9</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span class="cm-comment">1. create a new branch using **git branch &lt;branch-name&gt;**</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">10</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span class="cm-comment">2. switch to that branch using **git checkout &lt;branch-name&gt;**</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">11</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span cm-text="">&#8203;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">12</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span class="cm-comment">```</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">13</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span cm-text="">&#8203;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">14</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span class="cm-header cm-header-2">## Authors</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">15</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span cm-text="">&#8203;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">16</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span class="cm-strong">**Charles Swaleh**</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">17</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span cm-text="">&#8203;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">18</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span cm-text="">&#8203;</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">19</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;"><span class="cm-header cm-header-2">## License</span></span></pre></div><div style="position: relative;"><div class="CodeMirror-gutter-wrapper" style="left: -29px;"><div class="CodeMirror-linenumber CodeMirror-gutter-elt" style="left: 0px; width: 21px;">20</div></div><pre class=" CodeMirror-line "><span style="padding-right: 0.1px;">This software is licensed under the <span class="cm-link">[MIT]</span><span class="cm-string cm-url">(https://github.com/mashm3ll0w/learn-branching/blob/master/LICENSE.md)</span> License ©</span></pre></div></div></div></div></div></div><div style="position: absolute; height: 18px; width: 1px; border-bottom: 0px solid transparent; top: 514px;"></div><div class="CodeMirror-gutters" style="height: 532px; left: 0px;"><div class="CodeMirror-gutter CodeMirror-linenumbers" style="width: 29px;"></div></div></div></div>
          </div>
          <div class="col-md-6 full-height preview-dark-mode" style="overflow-y: auto;display:block;" id="previewPanel">
            <div id="markdown"><h1 id="git-branching">GIT BRANCHING</h1>
<h2 id="learn-git-branching">Learn Git Branching</h2>
<p>Introduce git branching and the powerful, efficient and time saving features that branching enables one to perform.</p>
<h2 id="how-to-use">How to use</h2>
<pre><code>1. create a new branch using **git branch &lt;branch-name&gt;**
2. switch to that branch using **git checkout &lt;branch-name&gt;**
</code></pre><h2 id="authors">Authors</h2>
<p><strong>Charles Swaleh</strong></p>
<h2 id="license">License</h2>
<p>This software is licensed under the <a href="https://github.com/mashm3ll0w/learn-branching/blob/master/LICENSE.md">MIT</a> License ©</p>
</div>
            <textarea id="htmlPreview" class="mdHtml"></textarea>
          </div>
      </section>
      <!-- Markdown Help Modal -->
      <div class="modal fade" id="myModal" role="dialog">
        <div class="modal-dialog">
          <!-- Modal content-->
          <div class="modal-content">
            <div class="modal-header">
              <button type="button" class="close" data-dismiss="modal">×</button>
              <h4 class="modal-title">Markdown Help</h4>
            </div>
            <div class="modal-body">
              <section class="modal--default__content" id="modal-body-region">
                <table class="markdown-help-content">
                  <tbody>
                      <tr>
                        <td><strong>Bold</strong></td>
                        <td>**bold**</td>
                      </tr>
                      <tr>
                        <td><i>Italics</i></td>
                        <td>*italics*</td>
                      </tr>
                      <tr>
                        <td><del>Strikethrough</del></td>
                        <td>~~strikethrough~~</td>
                      </tr>
                      <tr>
                        <td>Header</td>
                        <td># H1     ## H2     ### H3</td>
                      </tr>
                      <tr>
                        <td><li>item</li></td>
                        <td>* item</td>
                      </tr>
                      <tr>
                        <td>Blockquote</td>
                        <td>&gt; blockquote</td>
                      </tr>
                      <tr>
                        <td><span class="issue open">#123</span> (issue)</td>
                        <td>#123</td>
                      </tr>
                      <tr>
                        <td><a href="https://github.com/amitmerchant1990/electron-markdownify" target="_rick">Link</a></td>
                        <td>[title](http://)</td>
                      </tr>
                      <tr>
                        <td>Image</td>
                        <td>![alt](http://)</td>
                      </tr>
                      <tr>
                        <td><code>code</code></td>
                        <td>`code`</td>
                      </tr>
                      <tr>
                        <td>L<sup>a</sup>T<sub>e</sub>X</td>
                        <td>$$LaTeX code$$</td>
                      </tr>
                      <tr>
                        <td><pre style="display: inline-block; margin: 4px 0"><code><span class="keyword">var </span>code = <span class="string">"formatted"</span>;</code></pre></td>
                        <td style="line-height: 100%">``` <i style="color: rgba(0,0,0,0.5)">(shift+enter for line break)</i><br>var code = "formatted";<br>```</td>
                      </tr>
                  </tbody>
                </table>
              </section>
            </div>
            <div class="modal-footer">
              <button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
            </div>
          </div>
        </div>
      </div>

      <script>if (typeof module === 'object') {window.module = module; module = undefined;}</script>
      <script src="file:///home/bones/Desktop/cool-projects/markdownify-web/js/libs/jquery.min.js"></script>
      <script src="file:///home/bones/Desktop/cool-projects/markdownify-web/js/libs/bootstrap.min.js"></script>
      <script>if (window.module) module = window.module;</script>
      <script src="file:///home/bones/Desktop/cool-projects/markdownify-web/js/libs/marked.min.js"></script>
      <script src="file:///home/bones/Desktop/cool-projects/markdownify-web/js/libs/showdown.min.js"></script>
      <script src="file:///home/bones/Desktop/cool-projects/markdownify-web/js/libs/codemirror.js"></script>
      <script src="file:///home/bones/Desktop/cool-projects/markdownify-web/js/libs/placeholder.js"></script>
      <script src="file:///home/bones/Desktop/cool-projects/markdownify-web/js/libs/search.js"></script>
      <script src="file:///home/bones/Desktop/cool-projects/markdownify-web/js/libs/searchcursor.js"></script>
      <script src="file:///home/bones/Desktop/cool-projects/markdownify-web/js/libs/dialog.js"></script>
      <script src="file:///home/bones/Desktop/cool-projects/markdownify-web/js/libs/closebrackets.js"></script>
      <script src="file:///home/bones/Desktop/cool-projects/markdownify-web/js/markdown/markdown.js"></script>
      <script src="file:///home/bones/Desktop/cool-projects/markdownify-web/js/app.js"></script>
      <script src="file:///home/bones/Desktop/cool-projects/markdownify-web/js/format.js"></script>
      <script src="file:///home/bones/Desktop/cool-projects/markdownify-web/js/functions.js"></script>
      <script src="file:///home/bones/Desktop/cool-projects/markdownify-web/js/emoji.js"></script>
      <!-- Place this tag in your head or just before your close body tag. -->
      <script async="" defer="" src="./README_files/buttons.js"></script>
  

</body></html>
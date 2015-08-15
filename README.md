# syntaxhighlighter
Uses GitHub as a https server for Alex Gorbatchev's SyntaxHighlighter

Blogger (https://www.blogger.com/) is now more strict about using https and modifying script URLs.  This repository serves out Alex Gorbatchev's SyntaxHighlighter so Blogger can use Alex Gorbatchev's SyntaxHighlighter.  You can modify and paste the following code into your Blogger template to make SyntaxHighlighter work.

    <script language="javascript">
    function hook(el, cb) {
      if (cb) {
        if (el.readyState) { //IE
          el.onreadystatechange = function() {
            if ((el.readyState == &quot;loaded&quot;) || (el.readyState == &quot;complete&quot;)) {
              el.onreadystatechange = null;
              cb();
            }
          };
        } else {  //Others
          el.onload = function(){
            cb();
          };
        }
      }
    }
    function externalCss(url, cb) {
      var el = document.createElement(&quot;link&quot;);
      hook(el, cb);
      el.setAttribute(&quot;rel&quot;, &quot;stylesheet&quot;);
      el.setAttribute(&quot;type&quot;, &quot;text/css&quot;);
      el.setAttribute(&quot;href&quot;, url);
      document.head.appendChild(el);
    }
    function externalScript(url, cb) {
      var el = document.createElement(&#39;script&#39;);
      hook(el, cb);
      el.type = &#39;text/javascript&#39;;
      el.setAttribute(&#39;src&#39;, url);
      document.head.appendChild(el);
    }
    var path = &#39;https://cdn.rawgit.com/dwhey/syntaxhighlighter/master/&#39;;
    externalCss(path + &#39;shCore.css&#39;, function() {
    externalCss(path + &#39;shThemeEclipse.css&#39;, function() {
    externalScript(path + &#39;shCore.js&#39;, function() {
    externalScript(path + &#39;shBrushJScript.js&#39;, function() {
      SyntaxHighlighter.config.bloggerMode = true;
      SyntaxHighlighter.all();
    })})})});
    </script>


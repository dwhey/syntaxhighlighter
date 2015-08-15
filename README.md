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
      var el = document.createElement(&quot;script&quot;);
      hook(el, cb);
      el.type = &quot;text/javascript&quot;;
      el.setAttribute(&quot;src&quot;, url);
      document.head.appendChild(el);
    }
    var path = &quot;https://cdn.rawgit.com/dwhey/syntaxhighlighter/master/&quot;;
    externalCss(path + &quot;shCore.css&quot;, function() {
    externalCss(path + &quot;shThemeEclipse.css&quot;, function() {
    externalScript(path + &quot;shCore.js&quot;, function() {
    externalScript(path + &quot;shBrushJScript.js&quot;, function() {
      SyntaxHighlighter.config.bloggerMode = true;
      SyntaxHighlighter.all();
    })})})});
    </script>


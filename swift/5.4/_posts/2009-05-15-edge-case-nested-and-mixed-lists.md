---
author_profile: true
sidebar:
  title: "Swift"
  nav: sidebar-swift
title: "Edge Case: Nested and Mixed Lists"
categories: ["swift", "5.4"]
tags:
  - content
  - css
  - edge case
  - lists
  - markup
---

첫번째 포스트를 작성하고 있다.

## 소주제1

나만의 __멋진__ 블로그를 만들어야지.<br/>
화이팅!

```swift
print("hello blog")
```

이 문서의 title은 '{{ page.title }}' 이다!

다음 문서의 title은 '{{ page.title | append: "에 이어 두번째 포스트" }}' 이다!

<div id="disqus_thread"></div>
<script>
    /**
     *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT
     *  THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR
     *  PLATFORM OR CMS.
     *
     *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT:
     *  https://disqus.com/admin/universalcode/#configuration-variables
     */
    
    var disqus_config = function () {
        // Replace PAGE_URL with your page's canonical URL variable
        this.page.url = "{{ page.url | absolute_url }};";
        
        // Replace PAGE_IDENTIFIER with your page's unique identifier variable
        this.page.identifier = "{{ page.id }}";
    };
    
    (function() {  // REQUIRED CONFIGURATION VARIABLE: EDIT THE SHORTNAME BELOW
        var d = document, s = d.createElement('script');
        
        // IMPORTANT: Replace EXAMPLE with your forum shortname!
        s.src = 'https://{{ site.comments.disqus.shortname }}.disqus.com/embed.js';
        
        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>
    Please enable JavaScript to view the
    <a href="https://disqus.com/?ref_noscript" rel="nofollow">
        comments powered by Disqus.
    </a>
</noscript>

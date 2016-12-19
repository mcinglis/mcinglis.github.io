---
layout: default
title: Search Plugins and Privacy
tags: ['privacy']
---

The default Google search plugin on [Fedora](https://fedoraproject.org/)'s Firefox comes with lots of parameters and tracking information:

``` xml
<!-- This Source Code Form is subject to the terms of the Mozilla Public
   - License, v. 2.0. If a copy of the MPL was not distributed with this
   - file, You can obtain one at http://mozilla.org/MPL/2.0/. -->

<SearchPlugin xmlns="http://www.mozilla.org/2006/browser/search/">
<ShortName>Google</ShortName>
<Description>Google Search</Description>
<InputEncoding>UTF-8</InputEncoding>
<Url type="application/x-suggestions+json" method="GET" template="https://www.google.com/complete/search?client=firefox&amp;q={searchTerms}"/>
<Url type="text/html" method="GET" template="https://www.google.com/search">
  <Param name="q" value="{searchTerms}"/>
  <Param name="ie" value="utf-8"/>
  <Param name="oe" value="utf-8"/>
  <Param name="aq" value="t"/>
  <Param name="rls" value="{moz:distributionID}:{moz:locale}:{moz:official}"/>
  <MozParam name="client" condition="defaultEngine" trueValue="firefox-a" falseValue="firefox"/>
  <MozParam name="channel" condition="purpose" purpose="contextmenu" value="rcs"/>
  <MozParam name="channel" condition="purpose" purpose="keyword" value="fflb"/>
  <MozParam name="channel" condition="purpose" purpose="searchbar" value="sb"/>
  <MozParam name="channel" condition="purpose" purpose="homepage" value="np"/>
  <MozParam name="source" condition="purpose" purpose="homepage" value="hp"/>
</Url>
<SearchForm>https://www.google.com/</SearchForm>
</SearchPlugin>
```

I released [a bunch of OpenSearch plugins](/opensearch-plugins/index.html) today that respect your privacy, and only send the bare minimum amount of data to perform the search.

Enjoy!


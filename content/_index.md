---
title: Feast of Flavours
type: default
breadcrumbs: false
prev: /
next: /
sectionPagesMenu: main
---
## Explore
{{< cards >}}
  {{< card link="recipes" title="Recipes" icon="home" >}}
  {{< card link="restaurants" title="Restaurants" icon="heart" >}}
  {{< card link="cookbooks" title="Cookbooks" icon="book-open" >}}
  <!-- https://v1.heroicons.com/ -->
    {{< card link="about" title="About Us" icon="user-group" >}}
{{< /cards >}}
## Ethos
Food is not just eaten but experienced. Managed by culinary enthusiasts, our blog serves as a vibrant anthology of our food adventures. From the comfort of home-cooked meals to the excitement of new restaurant finds, we savour every bite and share our tales with you.
<!-- For more information, visit [Hextra](https://imfing.github.io/hextra). -->

{{- $page := .page }}
{{- $menuID := .menuID }}

{{- with index site.Menus $menuID }}
  <nav>
    <ul>
      {{- partial "inline/menu/walk.html" (dict "page" $page "menuEntries" .) }}
    </ul>
  </nav>
{{- end }}

{{- define "partials/inline/menu/walk.html" }}
  {{- $page := .page }}
  {{- range .menuEntries }}
    {{- $attrs := dict "href" .URL }}
    {{- if $page.IsMenuCurrent .Menu . }}
      {{- $attrs = merge $attrs (dict "class" "active" "aria-current" "page") }}
    {{- else if $page.HasMenuCurrent .Menu .}}
      {{- $attrs = merge $attrs (dict "class" "ancestor" "aria-current" "true") }}
    {{- end }}
    {{- $name := .Name }}
    {{- with .Identifier }}
      {{- with T . }}
        {{- $name = . }}
      {{- end }}
    {{- end }}
    <li>
      <a
        {{- range $k, $v := $attrs }}
          {{- with $v }}
            {{- printf " %s=%q" $k $v | safeHTMLAttr }}
          {{- end }}
        {{- end -}}
      >{{ $name }}</a>
      {{- with .Children }}
        <ul>
          {{- partial "inline/menu/walk.html" (dict "page" $page "menuEntries" .) }}
        </ul>
      {{- end }}
    </li>
  {{- end }}
{{- end }}



{{- range site.Menus.main }}
  <a href="{{ .URL }}">
    {{ .Name }}
    {{- with .Page }}
      {{- with .Params.version -}}
        ({{ . }})
      {{- end }}
    {{- end }}
  </a>
{{- end }}

The following is the [lookup order] for content views:

    /layouts/<TYPE>/<VIEW>.html
    /layouts/_default/<VIEW>.html
    /themes/<THEME>/layouts/<TYPE>/<VIEW>.html
    /themes/<THEME>/layouts/_default/<VIEW>.html


<main id="main">
  <div>
    <h1 id="title">{{ .Title }}</h1>
    {{ range .Pages }}
      {{ .Render "summary" }}
    {{ end }}
  </div>
</main>

<article class="post">
  <header>
    <h2><a href="{{ .RelPermalink }}">{{ .Title }}</a></h2>
    <div class="post-meta">{{ .Date.Format "Mon, Jan 2, 2006" }} - {{ .FuzzyWordCount }} Words </div>
  </header>
  {{ .Summary }}
  <footer>
  <a href='{{ .RelPermalink }}'>Read&nbsp;more&nbsp;&raquo;</a>
  </footer>
</article>


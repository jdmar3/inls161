# Assignment Breakdown

{% marginnote 'tab1' '*Table 1*: List of required course tasks' %}

| **Task** | **Components** | **%** | **Due date** |  
| :------- | :------------- | ----: | -----------: |{% for post in site.categories.assignments reversed %}{% if post.title %}
| {{ post.era }} | [{{ post.short_description }}]({{ post.url | prepend: site.baseurl }}) | {{ post.percentage }} | {{ post.start_date | date: "%b %-d at %H:%M" }} |{% endif %}{% endfor %}
---
title: Workshop Information
nav_title: Information
---

{% if site.workshop_type == "remote" %}
    {% include_relative workshop-information-files/workshop-structure.md %}
{% elsif site.workshop_type == "in-person" %}
    {% include_relative workshop-information-files/participant-information.md %}
{% endif %}

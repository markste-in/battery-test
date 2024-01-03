---
title: Lithium Ion
---
# All conducted Tests

<table>
  {% for row in site.data.lithium-ion %}
    {% if forloop.first %}
    <tr>
      {% for pair in row %}
        <th>{{ pair[0] | strip }}</th>
      {% endfor %}
    </tr>
    {% endif %}

    <tr>
      {% for pair in row %}
        {% assign column_name = pair[0] | strip %}
        {% assign column_value = pair[1] | strip %}
        
        {% if column_name == 'picture' %}
          <td><img src="{{ column_value }}" alt="Image" style="max-width: 200px; max-height: 150px;"></td>
        {% elsif column_name == 'result' %}
          {% if column_value == 'legit' %}
            <td style="background-color: #90ee90;">{{ column_value }}</td>
          {% elsif column_value == 'fraud' %}
            <td style="background-color: #ffcccb;">{{ column_value }}</td>
          {% else %}
            <td>{{ column_value }}</td>
          {% endif %}
        {% elsif column_name == 'source' %}
          {% if column_value contains 'http://' or column_value contains 'https://' %}
            <td><a href="{{ column_value }}">{{ column_value }}</a></td>
          {% else %}
            <td>{{ column_value }}</td>
          {% endif %}
       {% elsif column_name == 'report' %}
          {% if column_value != '' %}
            <td><a href="{{ site.baseurl }}{{ column_value }}">View Report</a></td>
          {% else %}
            <td>No Report Available</td> <!-- Or leave this empty if preferred -->
          {% endif %}
        {% else %}
          <td>{{ column_value }}</td>
        {% endif %}
      {% endfor %}
    </tr>
  {% endfor %}
</table>

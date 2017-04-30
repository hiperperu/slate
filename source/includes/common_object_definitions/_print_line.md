
## Print Line

> Sample object:

```json
{
    "align": "CENTER",
    "font": "A_REGULAR",
    "previous": "Welcome to",
    "content": "Hiper",
    "next": "!"
}
```

Model of print line object.

### Fields

* **align** <span class="param-type">Enum</span><br>
Alignment of the line.
<p>
    <span class="param-condition">Possible values:</span>
    <ul>
        <li><code>LEFT</code></li>
        <li><code>CENTER</code></li>
        <li><code>RIGHT</code></li>
    </ul>
</p>

* **font** <span class="param-type">Enum</span><br>
Font of the line.
<p>
    <span class="param-condition">Possible values:</span>
    <ul>
        <li><code>A_REGULAR</code></li>
        <li><code>B_REGULAR</code></li>
        <li><code>A_DOUBLE_HIGH</code></li>
        <li><code>B_DOUBLE_HIGH</code></li>
        <li><code>A_DOUBLE_WIDTH</code></li>
        <li><code>B_DOUBLE_WIDTH</code></li>
        <li><code>A_QUADRUPLE</code></li>
        <li><code>B_QUADRUPLE</code></li>
        <li><code>C_DOUBLE_HIGH</code></li>
        <li><code>C_DOUBLE_WIDTH</code></li>
        <li><code>C_QUADRUPLE</code></li>
    </ul>
</p>

* **previous** <span class="param-type">String</span><br>
Message to print before the content.
<p>
    <span class="param-condition">Maximum length:</span> <code>50</code>
</p>

* **content** <span class="param-type">String</span><br>
Message to print as content.
<p>
    <span class="param-condition">Maximum length:</span> <code>50</code>
</p>

* **next** <span class="param-type">String</span><br>
Message to print after the content.
<p>
    <span class="param-condition">Maximum length:</span> <code>50</code>
</p>

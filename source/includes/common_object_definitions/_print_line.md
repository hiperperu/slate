
## Print Line

> Sample model:

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

* **align** <span class="param-type">Enum</span> <br>Aligned of the line. <p>*Possible values*: <ul><li><code>LEFT</code></li><li><code>CENTER</code></li><li><code>RIGHT</code></li></ul></p>
* **font** <span class="param-type">Enum</span>  <br>Font of the line. <p>*Possible values*: <ul><li><code>A_REGULAR</code></li><li><code>B_REGULAR</code></li><li><code>A_DOUBLE_HIGH</code></li><li><code>B_DOUBLE_HIGH</code></li><li><code>A_DOUBLE_WIDTH</code></li><li><code>B_DOUBLE_WIDTH</code></li><li><code>A_QUADRUPLE</code></li><li><code>B_QUADRUPLE</code></li><li><code>B_QUADRUPLE</code></li><li><code>C_DOUBLE_HIGH</code></li><li><code>C_DOUBLE_WIDTH</code></li><li><code>C_QUADRUPLE</code></li></ul></p>
* **previous** <span class="param-type">String</span>  <br>Message to print before the content.
* **content** <span class="param-type">String</span>  <br>Message to print as content.
* **next** <span class="param-type">String</span>  <br>Message to print after the content.

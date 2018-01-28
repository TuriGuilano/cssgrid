# css grid notes

> implicit vs explicit

All the rows that we specify styles for are explicit rows.
All the other rows will be formatted based on the specified column grid with default hight styles. 
```
.container {
    display: grid;
    grid-gap: 20px;
    grid-template-columns: 200px 400px;
    grid-template-rows: 50px 100px 75px;
    /* sets hights for implicit defined rows to a height of 350px */
    grid-auto-rows: 350px;
}
```

> grid auto flow

When grid-auto-flow is being set to column the rows without specified styles are being added in the same row instead of on a new row.

You can then set the grid-auto-columns equal to a amount of px which will be adapted as the 'width' for the implicit created columns.

```
.container {
    display: grid;
    grid-gap: 20px;
    grid-template-columns: 400px 200px;
    grid-auto-flow: column;
    grid-auto-columns: 50px;
}
```
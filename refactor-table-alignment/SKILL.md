---
skill: refactor-table-alignment
version: "1.0.0"
type: "refactor_ui"
description: >
  Refactor table components to match enterprise UX alignment standards.
  Detects semantic column types and enforces alignment + formatting + width constraints.
tags: [enterprise, ui, table, alignment, formatting]
author: ChatGPT
---

## Trigger Conditions

Trigger when:

- Editing or refactoring table components in UI code.
- Table-like data structures detected.
- Column definitions present.

Matches patterns such as:

- `table`, `DataGrid`, `ColumnConfig`
- Ant Design / Element Plus / MUI Table components.

## Inputs

| Name       | Type   | Required | Description                     |
| ---------- | ------ | -------- | ------------------------------- |
| sourceCode | string | yes      | The UI source file content      |
| columnDefs | array  | optional | Explicit column definitions     |
| language   | string | no       | Code language (js/ts/vue/react) |

## Outputs

| Name            | Type   | Description             |
| --------------- | ------ | ----------------------- |
| transformedCode | string | Refactored code         |
| diff            | string | Unified diff of changes |
| report          | object | Alignment audit report  |

## Steps (Implementation)

1. **Parse code**
    - Use AST parser (Babel/TS) to find table definitions.

2. **Detect column semantics**
    - Semantic rules:
        - `index`: id / serial
        - `date` / `datetime`: date formats
        - `status`: tag/badge
        - `action`: button/icon columns
        - `numeric`: numbers/metrics
        - `text`: semantic text

3. **Resolve alignment**
    - Map semantics → alignment:
        - `index`: center
        - `date/datetime`: center
        - `status`: center
        - `action`: center
        - `numeric`: right
        - `text`: left

4. **Apply formatting**
    - Numeric: add formatting functions
    - Date: enforce consistent `YYYY-MM-DD` or `YYYY-MM-DD HH:mm`

5. **Enforce width**
    - Inject fixed widths where required

6. **Output transformed code + diff + report**

---

## Rules (Hard Constraints)

### Alignment Rules

| Semantic | Alignment |
| -------- | --------- |
| index    | center    |
| date     | center    |
| datetime | center    |
| status   | center    |
| action   | center    |
| numeric  | right     |
| text     | left      |

### Format Constraints

- Numeric values must use thousand separators
- Numeric columns must have consistent decimal places
- Date formats must be one style per column

### Width Constraints

- Index: 48–64px fixed
- Date only: ~120px
- Date + time: 160–180px
- Action: 120–160px fixed

### Prohibitions

- Do not override sorting/filtering/pagination
- Do not left-align numeric data
- Do not mix alignments within the same semantic type
- Do not center all columns globally

---

## Examples

### Before

````js
{
  title: "Amount",
  dataIndex: "amount",
  key: "amount"
}


### After

```js
{
  title: "Amount",
  dataIndex: "amount",
  key: "amount",
  align: "right",
  render: v => formatNumber(v, { thousands: true, decimals: 2 })
}
````

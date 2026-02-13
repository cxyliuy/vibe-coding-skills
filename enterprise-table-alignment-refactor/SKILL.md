# 🧩 Skill: Enterprise Table Alignment Refactor

> Enforce enterprise UX table alignment and numeric formatting standards
> without breaking existing functionality.

## 📦 Metadata

---
name: enterprise-table-alignment-refactor
type: ui-refactor
scope: component-level
risk: low
preserves_behavior: true
---

## 🎯 Purpose

Improve visual scanability, numeric comparability, and information
hierarchy by applying strict semantic alignment rules.

## 🧠 Activation Conditions

Trigger when working with table or grid components (HTML tables, Ant
Design, Element Plus, MUI DataGrid, or custom systems).

## 📐 Alignment Standards

### Center Align

-   Index / Serial Number
-   Date / Date-Time
-   Status (tag UI)
-   Action buttons

### Left Align

-   Name
-   Title
-   Description
-   Category
-   Address
-   All readable text fields

### Right Align

-   Amount
-   Price
-   Quantity
-   KPI
-   Percentages
-   Statistics

With thousand separators and consistent decimals.

## 📏 Width Constraints

  Column      Width
----------- ------------
  Index       48--64px
  Date        \~120px
  Date+Time   160--180px
  Action      120--160px

## 🚫 Prohibited

-   Global centering
-   Numeric left alignment
-   Mixed semantic alignment
-   Breaking sorting/filtering/pagination

## 🛠️ Refactor Flow

1.  Detect column semantics\
2.  Apply alignment + formatting\
3.  Enforce width rules

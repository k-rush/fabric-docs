---
title: Query using the visual query editor
description: Learn how to use the visual query editor.
author: prlangad
ms.author: prlangad
ms.reviewer: wiassaf
ms.date: 05/23/2023
ms.topic: how-to
ms.custom: build-2023
ms.search.form: Query editor # This article's title should not change. If so, contact engineering.
---
# Query using the visual query editor

**Applies to:** [!INCLUDE[fabric-se-and-dw](includes/applies-to-version/fabric-se-and-dw.md)]

You can [query the data](query-warehouse.md) in your warehouse with multiple tools, including the visual query editor and the [SQL query editor](sql-query-editor.md). This article describes how to use the visual query editor to quickly and efficiently write queries, and suggestions on how best to see the information you need.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Visual query editor in the Fabric portal

The visual query editor provides an easy visual interface to write queries against the data in your warehouse.

Once you've loaded data into your warehouse, you can use the visual query editor to create queries to analyze your data. You can use the visual query editor for a no-code experience to create your queries.

There are two ways to get to the visual query editor:

In the ribbon, create a new query using the **New visual query** button, as shown in the following image.

:::image type="content" source="media\visual-query-editor\new-visual-query.png" alt-text="Screenshot showing where to find the New query menu in the Data preview view." lightbox="media\visual-query-editor\new-visual-query.png":::

To create a query, drag and drop tables from the **Object explorer** on the left onto the canvas. Once you drag one or more tables onto the canvas, you can use the visual experience to design your queries. The warehouse editor uses the Power Query diagram view experience to enable you to easily query and analyze your data. Learn more about [Power Query diagram view](/power-query/diagram-view).

As you work on your visual query, the queries are automatically saved every few seconds. A "saving indicator" appears in your query tab to indicate that your query is being saved.

The following animated gif shows the merging of two tables using a no-code visual query editor. First, the `DimCity` then `FactSale` are dragged from the **Explorer** into the visual query editor. Then, the **Merge** Power Query operator is used to join them on a common key.


:::image type="content" source="media\visual-query-editor\visual-query-editor.gif" alt-text="Animation of the results of a sample query to merge two tables using the visual query editor." lightbox="media\visual-query-editor\visual-query-editor.gif":::

When you see results, you can use **Download Excel file** to view results in Excel or **Visualize results** to create report on results.

## Create a cross-warehouse query in visual query editor

For more information on cross-warehouse querying, see [Cross-warehouse querying](query-warehouse.md#write-a-cross-database-query).

- To create a cross-warehouse query, drag and drop tables from added warehouses and add merge activity. For example, in the following image example, `store_sales` is added from `sales` warehouse and it's merged with `item` table from `marketing` warehouse.

:::image type="content" source="media\visual-query-editor\cross-warehouse-query-visual-query-editor.png" alt-text="Screenshot of sample cross-warehouse query between sales and marketing database and Power Query activities." lightbox="media\visual-query-editor\cross-warehouse-query-visual-query-editor.png":::

## Limitations with visual query editor

- In the visual query editor, you can only run DQL (Data Query Language) or read-only [SELECT](/sql/t-sql/queries/select-transact-sql?view=fabric&preserve-view=true) statements. DDL or DML are not supported.
- Only a subset of Power Query operations that support Query folding are currently supported.

## Next steps

- [How-to: Query the Warehouse](query-warehouse.md)
- [Query using the SQL Query editor](sql-query-editor.md)

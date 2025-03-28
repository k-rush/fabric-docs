---
title: OneLake security
description: OneLake uses a layered security model built around the organizational structure of components within Microsoft Fabric. Learn more about OneLake security.
ms.reviewer: eloldag
ms.author: aamerril
author: aamerril
ms.topic: conceptual
ms.custom: build-2023, build-2023-dataai, build-2023-fabric
ms.date: 05/23/2023
---

# OneLake security

OneLake uses a layered security model built around the organizational structure of components within Microsoft Fabric. Security is derived from Azure Active Directory (Azure AD) authentication and is compatible with user identities, service principals, and managed identities. Using Azure AD and Fabric components, you can build out robust security mechanisms across OneLake, ensuring that you keep your data safe while also reducing copies and minimizing complexity.

:::image type="content" source="media\onelake-security\onelake-structure.png" alt-text="Diagram showing the structure of a data lake connecting to separately secured containers." lightbox="media\onelake-security\onelake-structure.png":::

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Workspace security

The workspace is the primary security boundary for data within OneLake. Each workspace represents a single domain or project area where teams can collaborate on data. Security in the workspace is managed through Fabric workspace roles. Learn more about Fabric role-based access control (RBAC): [Workspace roles](../get-started/roles-workspaces.md)
  
Workspace roles in Fabric grant the following permissions in OneLake.

| **Capability** | **Admin** | **Member** | **Contributor** | **Viewer** |
|---|---|---|---|---|
| View files in OneLake | Yes | Yes | Yes | No |
| Write files in OneLake | Yes | Yes | Yes | No |

## Compute-specific security

Some compute engines in Fabric have their own security models. For example, Fabric Warehouse lets users define access using T-SQL statements. Compute-specific security is always enforced when you access data using that engine, but those conditions may not apply to users in certain Fabric roles when they access OneLake directly. See the documentation for Warehouse, Real-time analytics, and Power BI datasets for more details on what types of compute security can be defined. 

As a rule, users in the Viewer role can only access data through select compute engines and any security rules defined in those engines apply.  All other roles have direct OneLake access, allowing them to query data through Spark, APIs, or a OneLake File Explorer. However, compute-specific security still applies to those users when accessing data through that compute engine.

**Example:** Martha is an administrator for a Fabric workspace and Pradeep is a Viewer. Martha wants to restrict access to certain tables in LakehouseA. She connects to SQL and defines object level security using GRANT and DENY statements. When Pradeep accesses the data through SQL he is only able to see the tables from LakehouseA that he was granted access to.

## Shortcut security

Shortcuts in Microsoft Fabric allow for greatly simplified data management, but have some security considerations to note. For information on managing shortcut security see this [document](onelake-shortcuts.md#types-of-shortcuts).

## Authentication

OneLake uses Azure Active Directory (Azure AD) for authentication; you can use it to give permissions to user identities and service principals. OneLake automatically extracts the user identity from tools, which use Azure AD authentication and map it to the permissions you set in the Fabric portal.

> [!NOTE]
> To use service principals in a Fabric tenant, a tenant administrator must enable Service Principal Names (SPNs) for the entire tenant or specific security groups.

:::image type="content" source="media\onelake-security\admin-portal-tenant-settings.png" alt-text="Screenshot showing the Developer settings options on the Tenant setting screen." lightbox="media\onelake-security\admin-portal-tenant-settings.png":::

## Private links

Fabric doesn’t currently support private link access to OneLake data via non-Fabric products and Spark.

## Allow apps running outside of Fabric to access data via OneLake

OneLake provides the ability to restrict access to data from applications running outside of Fabric environments. Admins can find the setting in the tenant admin portal.
When this switch is turned ON, data can be accessed via all sources. When this switched is turned OFF, data cannot be accessed via applications running outside of Fabric environments. For example, data can be access via applications like Azure Databricks, custom applications using ADLS APIs, or OneLake file explorer.

## Next steps

- [OneLake file explorer](onelake-file-explorer.md)
- [Workspace roles](../get-started/roles-workspaces.md)  

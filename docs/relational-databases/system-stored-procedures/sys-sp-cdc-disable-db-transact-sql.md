---
title: "sys.sp_cdc_disable_db (Transact-SQL)"
description: "sys.sp_cdc_disable_db (Transact-SQL)"
author: markingmyname
ms.author: maghan
ms.date: "03/15/2017"
ms.service: sql
ms.subservice: system-objects
ms.topic: "reference"
f1_keywords:
  - "sp_cdc_disable_db"
  - "sys.sp_cdc_disable_db_TSQL"
  - "sp_cdc_disable_db_TSQL"
  - "sys.sp_cdc_disable_db"
helpviewer_keywords:
  - "sp_cdc_disable_db"
  - "sys.sp_cdc_disable_db"
  - "change data capture [SQL Server], disabling databases"
dev_langs:
  - "TSQL"
---
# sys.sp_cdc_disable_db (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Disables change data capture for the current database. Change data capture is not available in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
**Applies to**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ( [!INCLUDE[sql2008-md](../../includes/sql2008-md.md)] through [current version](/troubleshoot/sql/general/determine-version-edition-update-level)).  
  
 :::image type="icon" source="../../includes/media/topic-link-icon.svg" border="false"::: [Transact-SQL syntax conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## Syntax  
  
```sql  
sys.sp_cdc_disable_db  
```  
  
## Return Code Values  
 **0** (success) or **1** (failure)  
  
## Result Sets  
 None  
  
## Remarks  
 **sys.sp_cdc_disable_db** disables change data capture for all tables in the database currently enabled. All system objects related to change data capture, such as change tables, jobs, stored procedures and functions, are dropped. The **is_cdc_enabled** column for the database entry in the [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) catalog view is set to 0.  
  
> [!NOTE]  
>  If there are many capture instances defined for the database at the time change data capture is disabled, a long running transaction can cause the execution of sys.sp_cdc_disable_db to fail. This problem can be avoided by disabling the individual capture instances by using sys.sp_cdc_disable_table before running sys.sp_cdc_disable_db.  
  
## Permissions  
 Requires membership in the **sysadmin** fixed server role for Change Data Capture on Azure SQL Managed Instance or SQL Server. Requires membership in the **db_owner** for Change Data Capture on Azure SQL Database.  
  
## Examples  
 The following example disables change data capture for the `AdventureWorks2012` database.  
  
```sql  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_disable_db;  
GO  
```  
  
## See Also  
 [sys.sp_cdc_enable_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql.md)   
 [sys.sp_cdc_disable_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-table-transact-sql.md)  
  

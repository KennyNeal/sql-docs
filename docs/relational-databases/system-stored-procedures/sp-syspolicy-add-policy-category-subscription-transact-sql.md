---
title: "sp_syspolicy_add_policy_category_subscription (Transact-SQL)"
description: "sp_syspolicy_add_policy_category_subscription (Transact-SQL)"
author: VanMSFT
ms.author: vanto
ms.date: "03/14/2017"
ms.service: sql
ms.subservice: system-objects
ms.topic: "reference"
f1_keywords:
  - "sp_syspolicy_add_policy_category_subscription"
  - "sp_syspolicy_add_policy_category_subscription_TSQL"
helpviewer_keywords:
  - "sp_syspolicy_add_policy_category_subscription"
dev_langs:
  - "TSQL"
---
# sp_syspolicy_add_policy_category_subscription (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Adds a policy category subscription to the specified database.  
  
 :::image type="icon" source="../../includes/media/topic-link-icon.svg" border="false"::: [Transact-SQL syntax conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## Syntax  
  
```  
  
sp_syspolicy_add_policy_category_subscription [ @target_type = ] 'target_type'  
    , [ @target_object = ] 'target_object'  
    , [ @policy_category = ] 'policy_category'  
    [ , [ @policy_category_subscription_id = ] policy_category_subscription_id OUTPUT ]  
```  
  
## Arguments  
`[ @target_type = ] 'target_type'`
 Is the target type of the category subscription. *target_type* is **sysname**, is required, and must be set to 'DATABASE'.  
  
`[ @target_object = ] 'target_object'`
 Is the name of the database that will subscribe to the category. *target_object* is **sysname**, and is required.  
  
`[ @policy_category = ] 'policy_category'`
 Is the name of the policy category to subscribe to. *policy_category* is **sysname**, and is required.  
  
 To obtain values for *policy_category*, query the msdb.dbo.syspolicy_policy_categories system view.  
  
`[ @policy_category_subscription_id = ] policy_category_subscription_id`
 Is the identifier for the category subscription. *policy_category_subscription_id* is **int**, and is returned as OUTPUT.  
  
## Return Code Values  
 **0** (success) or **1** (failure)  
  
## Remarks  
 You must run sp_syspolicy_add_policy_category_subscription in the context of the msdb system database.  
  
 If you specify a policy category that does not exist, a new policy category is created and the subscription is mandated for all databases when you execute the stored procedure. If you then clear the mandated subscription for the new category, the subscription will only apply for the database that you specified as the *target_object*. For more information about how to change a mandated subscription setting, see [sp_syspolicy_update_policy_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-transact-sql.md).  
  
## Permissions  
 This stored procedure runs in the context of the current owner of the stored procedure.  
  
## Examples  
 The following example configures the specified database to subscribe to a policy category that is named 'Table Naming Policies'.  
  
```  
EXEC msdb.dbo.sp_syspolicy_add_policy_category_subscription @target_type = N'DATABASE'  
, @target_object = N'AdventureWorks2012'  
, @policy_category = N'Table Naming Policies';  
  
GO  
```  
  
## See Also  
 [Policy-Based Management Stored Procedures &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_update_policy_category_subscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-update-policy-category-subscription-transact-sql.md)   
 [sp_syspolicy_unsubscribe_from_policy_category &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-unsubscribe-from-policy-category-transact-sql.md)  
  
  

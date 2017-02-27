---
title: "IDebugCustomAttributeQuery | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery-Schnittstelle"
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugCustomAttributeQuery
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt eine Abfrage für benutzerdefinierte Attribute auf eine Methode oder einen Typ dar.  
  
## Syntax  
  
```  
IDebugCustomAttributeQuery : IUnknown  
```  
  
## Methoden  
 Diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[\[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|Ruft ein benutzerdefiniertes angegebenes Attribut Name ab.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|Bestimmt im angegebenen benutzerdefinierten Attributs definiert ist.|  
  
## Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
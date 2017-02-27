---
title: "IDebugCustomAttributeQuery2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomAttributeQuery2"
helpviewer_keywords: 
  - "IDebugCustomAttributeQuery-Schnittstelle"
  - "IDebugCustomAttributeQuery2-Schnittstelle"
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugCustomAttributeQuery2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt das Vorhandensein eines benutzerdefinierten Attributs für dieses Feld und, sofern vorhanden, gibt die attributierten Informationen zurück.  
  
## Syntax  
  
```  
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery  
```  
  
## Hinweise für Implementierer  
 Ein Symbol Anbieter implementiert diese Schnittstelle für dasselbe Objekt, das [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) implementiert, um benutzerdefinierte Attribute zu unterstützen.  
  
## Hinweise für Aufrufer  
 Verwenden Sie [QueryInterface](/visual-cpp/atl/queryinterface) , um diese Schnittstelle aus der [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle zu erhalten.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle sind die Methoden der **IDebugCustomAttributeQuery\-Schnittstelle** an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Bestimmt, ob sich ein benutzerdefiniertes Attribut anhand des Namens vorhanden ist.|  
|[\[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Ruft die Attributinformationen für das angegebene benutzerdefinierte Attribut ab.|  
  
 Zusätzlich zu den **IDebugCustomAttributeQuery\-Methoden**`IDebugCustomAttributeQuery2` die folgende Methode implementiert wird:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Ruft einen Enumerator für alle benutzerdefinierten Attribute ab, die an dieses Feld angefügt werden.|  
  
## Hinweise  
 Die [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)\-Methode kann einen Enumerator für alle benutzerdefinierten Attribute zurück, die für dieses Feld definierten.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
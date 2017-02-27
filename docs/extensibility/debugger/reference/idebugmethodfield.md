---
title: "IDebugMethodField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField"
helpviewer_keywords: 
  - "IDebugMethodField-Schnittstelle"
ms.assetid: a7dc9030-fc98-4cf1-b943-37a4003300b6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugMethodField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle beschreibt eine Methode.  
  
## Syntax  
  
```  
IDebugMethodField : IDebugContainerField  
```  
  
## Hinweise für Implementierer  
 Ein Symbol Anbieter implementiert diese Schnittstelle für dasselbe Objekt, das die [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)\-Schnittstelle implementiert.  Diese Schnittstelle ist eine Spezialisierung, die eine Methode darstellt.  
  
## Hinweise für Aufrufer  
 Verwenden Sie [QueryInterface](/visual-cpp/atl/queryinterface) , um diese Schnittstelle aus der [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)\-Schnittstelle abzurufen, wenn [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)`FIELD_TYPE_METHOD`zurückgibt.  Darüber hinaus geben die Methoden, [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md), [GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)und alle [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md), die `IDebugMethodField`\-Schnittstelle zurück.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden für den [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) und Schnittstellen implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)|Erstellt einen Enumerator für die Parameter der Methode.|  
|[GetThis](../../../extensibility/debugger/reference/idebugmethodfield-getthis.md)|Ruft den „this“ \- Zeiger des Objekts ab, das die Methode enthält.|  
|[EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)|Erstellt einen Enumerator für alle lokalen Variablen der Methode.|  
|[EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)|Erstellt einen Enumerator für ausgewählte lokale Variablen der Methode.|  
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugmethodfield-iscustomattributedefined.md)|Bestimmt, ob ein bestimmtes benutzerdefiniertes Attribut definiert wurde.|  
|[EnumStaticLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumstaticlocals.md)|Erstellt einen Enumerator für statische lokale Variablen der Methode.|  
|[GetGlobalContainer](../../../extensibility/debugger/reference/idebugmethodfield-getglobalcontainer.md)|Ruft den globalen Container der Methode ab.|  
|[EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)|Erstellt einen Enumerator für den Typ jedes Arguments, das zum Aufrufen der Methode benötigt wird.|  
  
## Hinweise  
 Eine Methode kann Parameter und lokale Variablen enthalten.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
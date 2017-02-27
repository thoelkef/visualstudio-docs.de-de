---
title: "IDebugPropertyField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPropertyField"
helpviewer_keywords: 
  - "IDebugPropertyField-Schnittstelle"
ms.assetid: b50edb2c-fb8d-4def-993d-17d23d2027c1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPropertyField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt Funktionen bereit, die das Abrufen und Festlegen einer Eigenschaft ermöglichen.  
  
## Syntax  
  
```  
IDebugPropertyField : IDebugContainerField  
```  
  
## Hinweise für Implementierer  
 Ein Symbol Anbieter implementiert diese Schnittstelle für dasselbe Objekt, das [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)implementiert.  Diese Schnittstelle ist eine Spezialisierung, die das Konzept von Eigenschaften für eine Klasse unterstützt.  
  
## Hinweise für Aufrufer  
 [QueryInterface](/visual-cpp/atl/queryinterface) Verwendung dieser Schnittstelle aus der [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)\-Schnittstelle abzurufen, wenn die [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)\-Methode `FIELD_KIND_PROP`zurückgibt.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden für den [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) und Schnittstellen implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)|Ruft die Methode ab, mit der die Eigenschaft abgerufen werden soll.|  
|[GetPropertySetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertysetter.md)|Ruft die Methode ab, die die Eigenschaft festlegt.|  
  
## Hinweise  
 Eine Eigenschaft ist ein verwaltetes Code Konzept und stellt eine Möglichkeit dar, die als Variable behandelt wird.  Eigenschaften sind nicht in nicht verwaltetem C\+\+.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
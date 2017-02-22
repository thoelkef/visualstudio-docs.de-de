---
title: "IDebugClassField | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField"
helpviewer_keywords: 
  - "IDebugClassField-Schnittstelle"
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt eine Klasse als Typ dar.  
  
## Syntax  
  
```  
IDebugClassField : IDebugContainerField  
```  
  
## Hinweise für Implementierer  
 Ein Symbol Anbieter implementiert diese Schnittstelle für dasselbe Objekt, das die [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)\-Schnittstelle implementiert.  Diese Schnittstelle ist eine Spezialisierung, die einen Klassentyp darstellt.  
  
## Hinweise für Aufrufer  
 Einige Schnittstellen verfügen über Methoden, die diese Schnittstelle einschließlich [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)und [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)zurückgeben können.  Außerdem können Sie [QueryInterface](/visual-cpp/atl/queryinterface) verwenden, um diese Schnittstelle aus der [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)\-Schnittstelle abzurufen, wenn die [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)\-Methode das Flag `FIELD_TYPE_CLASS`zurückgibt.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden für den [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) und Schnittstellen implementiert diese Schnittstelle Folgendes:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Erstellt einen Enumerator für die Basisklasse dieser Klasse.|  
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Bestimmt, ob eine bestimmte Schnittstelle in der Klasse definiert ist.|  
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Erstellt einen Enumerator für die geschachtelte Klassen dieser Klasse.|  
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Ruft die Klasse ab, die diese Klasse enthalten ist.|  
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Erstellt einen Enumerator für die Schnittstellen, die von dieser Klasse implementiert werden.|  
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Erstellt einen Enumerator für die Konstruktoren dieser Klasse.|  
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Ruft den Namen des standardmäßigen Indexers ab.|  
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Erstellt einen Enumerator für die geschachtelten Enumeratoren dieser Klasse.|  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
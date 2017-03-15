---
title: "IDebugEnumField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField"
helpviewer_keywords: 
  - "IDebugEnumField-Schnittstelle"
ms.assetid: 42f685bf-0f39-47f4-98b0-6022efe2bf97
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugEnumField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Enumerationstyp dar.  
  
## Syntax  
  
```  
IDebugEnumField : IDebugContainerField  
```  
  
## Hinweise für Implementierer  
 Ein Symbol für implementiert diese Schnittstelle, um eine Enumeration dargestellt werden.  
  
## Hinweise für Aufrufer  
 Verwenden Sie [QueryInterface](/visual-cpp/atl/queryinterface) , um diese Schnittstelle aus der [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle abzurufen, wenn [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)`FIELD_TYPE_ENUM`zurückgibt.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden für den `IDebugField``IDebugContainerField` und Schnittstellen implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetUnderlyingSymbol](../../../extensibility/debugger/reference/idebugenumfield-getunderlyingsymbol.md)|Gibt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) zurück, der den Namen für den Enumerationstyp beschreibt.|  
|[GetStringFromValue](../../../extensibility/debugger/reference/idebugenumfield-getstringfromvalue.md)|Gibt den Namen der Enumerationskonstante zurück, die dem angegebenen Wert zugeordnet ist.|  
|[GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)|Gibt den Wert zurück, der dem angegebenen Enumeration konstantennamen zugeordnet ist.|  
|[GetValueFromStringCaseInsensitive](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstringcaseinsensitive.md)|Gibt den Wert zurück, der zugeordnet werden soll, mit dem angegebenen Enumeration konstantennamen aber die Groß\-\/Kleinschreibung ignoriert wird.|  
  
## Hinweise  
 Es ist das zugrunde liegende Symbol, das tatsächlich zu einem Speicherort mit [Binden](../../../extensibility/debugger/reference/idebugbinder-bind.md)gebunden ist.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [Binden](../../../extensibility/debugger/reference/idebugbinder-bind.md)
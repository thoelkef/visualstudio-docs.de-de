---
title: "IDebugPointerField | Microsoft Docs"
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
  - "IDebugPointerField"
helpviewer_keywords: 
  - "IDebugPointerField-Schnittstelle"
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPointerField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Zeigertyp dar.  
  
## Syntax  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## Hinweise für Implementierer  
 Der Symbol für implementiert diese Schnittstelle, um einen Zeiger darzustellen.  
  
## Hinweise für Aufrufer  
 Verwenden Sie [QueryInterface](/visual-cpp/atl/queryinterface) , um diese Schnittstelle aus der [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle abzurufen, wenn [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)`FIELD_TYPE_POINTER`zurückgibt.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden für den `IDebugField` und Schnittstellen implementiert diese Schnittstelle `IDebugContainerField` die folgende Methode:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Gibt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) zurück, das das Ziel des Zeigers beschreibt.|  
  
## Hinweise  
 In C\/C\+\+ kann ein Zeiger ein Container sein, wenn er mit Arraynotation verwendet wird.  Beispielsweise verfügt ein angegebenes `char *pString`, `pString` einen Typ Zeiger auf `char`.  `pString[3]` hat den Typ eines Containers, der ein Zeiger auf `char` handelt, der das vierte Element dieses Containers verweist.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
---
title: "IDebugGenericParamField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugGenericParamField-Schnittstelle"
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugGenericParamField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt einen Parameter für einen generischen Typ von verwaltetem Code dar.  
  
## Syntax  
  
```  
IDebugGenericParamField : IDebugField  
```  
  
## Hinweise für Implementierer  
 Wird für die Unterstützung von Generika.  
  
## Methoden  
 Zusätzlich zu den Methoden der [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Gibt die Anzahl der Einschränkungen zurück, die bei diesem generischen Parameter zugeordnet sind.|  
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Ruft die Einschränkungen ab, die bei diesem generischen Parameter zugeordnet sind.|  
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Ruft die Flags für diesen generischen Parameter ab.|  
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Ruft den Index dieses generischen Parameters ab.|  
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Ruft den Namen des generischen Parameters ab.|  
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Ruft den Besitzer dieses generischen Typ\- oder Methoden Parameters ab.|  
  
## Anforderungen  
 Header: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
---
title: "IDebugContainerField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugContainerField"
helpviewer_keywords: 
  - "IDebugContainerField-Schnittstelle"
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugContainerField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt ein Symbol oder einen Typ dar, die ein Container für andere Symbole oder Typen handelt.  
  
## Syntax  
  
```  
IDebugContainerField : IDebugField  
```  
  
## Hinweise für Implementierer  
 Ein Symbol Anbieter implementiert diese Schnittstelle für dasselbe Objekt, das die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle implementiert.  Diese Schnittstelle ist auch die Basisklasse für alle Schnittstellen, die Container darstellen.  
  
## Hinweise für Aufrufer  
 Viele Methoden in zahlreichen Schnittstellen geben diese Schnittstelle zurück.  Da dies eine Basisklasse für alle Container handelt, werden mehr spezialisierte Schnittstellen von dieser Schnittstelle abgerufen, indem ein [QueryInterface](/visual-cpp/atl/queryinterface)verwenden.  Zu diesen Schnittstellen gehören [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)und [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden der [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle implementiert diese Schnittstelle die folgende Methode:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[\[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Erstellt einen Enumerator für die Felder des Containers.|  
  
## Hinweise  
 Arrays \(Container für Variablen\) für Container \(Klassen, Methoden und Variablen\) und Methoden \(Container für Parameter und lokale Variablen\) sind alle Beispiele von Containern.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
---
title: "IEnumDebugObjects | Microsoft Docs"
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
  - "IEnumDebugObjects"
helpviewer_keywords: 
  - "IEnumDebugObjects-Schnittstelle"
ms.assetid: 0950364c-6c8a-4b6c-ba37-c6aa359fa72c
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugObjects
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt eine Auflistung von Objekten, die Implementierung der [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle.  
  
## Syntax  
  
```  
IEnumDebugObjects : IUnknown  
```  
  
## Hinweise für Implementierer  
 Die Auswertung eines Ausdrucks implementiert diese Schnittstelle, um Gruppen von Objekten bereitstellen, die implementieren die [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Schnittstelle. Beachten Sie, dass dies keine standardmäßige COM\-Enumeration wegen des Vorhandenseins der [GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md) Methode.  
  
## Hinweise für Aufrufer  
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md) gibt diese Schnittstelle.  
  
## Methoden in Vtable\-Reihenfolge  
 Diese Schnittstelle implementiert die folgenden Methoden.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Weiter](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)|Ruft den nächsten Satz von [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekte aus der Enumeration.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugobjects-skip.md)|Überspringt eine angegebene Anzahl von Einträgen.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugobjects-reset.md)|Setzt die Enumeration auf den ersten Eintrag zurück.|  
|[Klonen](../../../extensibility/debugger/reference/ienumdebugobjects-clone.md)|Ruft eine Kopie der aktuellen Enumeration.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugobjects-getcount.md)|Ruft die Anzahl der Einträge in der Enumeration ab.|  
  
## Hinweise  
 Diese Schnittstelle ermöglicht ein Debugmodul an eine Reihe von Objekten in einem Array durchlaufen.  
  
## Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetElements](../../../extensibility/debugger/reference/idebugarrayobject-getelements.md)
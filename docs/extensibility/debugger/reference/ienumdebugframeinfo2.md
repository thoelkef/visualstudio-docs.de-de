---
title: "IEnumDebugFrameInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFrameInfo2"
helpviewer_keywords: 
  - "IEnumDebugFrameInfo2"
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle listet [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen auf.  
  
## Syntax  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um eine Liste von Strukturen bereitzustellen, die die aktuelle Aufrufliste beschreibt.  
  
## Hinweise für Aufrufer  
 Visual Studio ruft [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) auf, um diese Schnittstelle immer dann, wenn ein Haltepunkt beenden oder eine Ausnahme auftritt in einem Programm, das gedebuggt wird.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IEnumDebugFrameInfo2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Weiter](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Ruft eine angegebene Anzahl [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen in der Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Überspringt eine angegebene Anzahl [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen in der Enumerationsfolge.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[Klonen](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Ruft die Anzahl der [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen in einem Enumerator ab.|  
  
## Hinweise  
 Visual Studio erhält diese Schnittstelle wie der erste Schritt zum Behandeln eines Haltepunkts, der USER\-generierten der Ausnahme oder Anhalten für das Programm, das gedebuggt wird.  Die Liste der [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) Strukturen stellt die aktuelle Aufrufliste mit dem aktuellen Funktionsaufruf Anfang der Liste und dem ältesten Funktionsaufruf am Ende der Liste dar.  Jedes `FRAMEINFO` stellt einen Stapelrahmen, einen Kontext dar, in der Ausdrücke ausgewertet werden können und lokale Variablen betrachtet werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
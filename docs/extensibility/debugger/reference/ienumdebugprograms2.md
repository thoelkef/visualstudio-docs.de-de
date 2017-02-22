---
title: "IEnumDebugPrograms2 | Microsoft Docs"
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
  - "IEnumDebugPrograms2"
helpviewer_keywords: 
  - "IEnumDebugPrograms2"
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle listet die Programme aufgeführt, die in die Debugsitzung der derzeit ausgeführt werden.  
  
## Syntax  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um eine Liste von Programmen bereitzustellen, die von DE gedebuggt werden.  
  
## Hinweise für Aufrufer  
 Visual Studio ruft [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) an, die zum Abrufen dieser Schnittstelle.  [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) wird nicht von Visual Studio.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IEnumDebugPrograms2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Weiter](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Ruft eine angegebene Anzahl von Programmen in der Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Überspringt eine angegebene Anzahl von Programmen in der Enumerationsfolge.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[Klonen](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Ruft die Anzahl von Programmen in einem Enumerator ab.|  
  
## Hinweise  
 Visual Studio verwendet diese Schnittstelle:  
  
-   Füllen Sie das **Module** Fenster \(durch Aufrufen von [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) und [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) für jedes Programm aufrufen.\)  
  
-   Füllen Sie die **An den Prozess anhängen** Liste nach oben \(durch Aufrufen von `IDebugProcess2::EnumPrograms` und [QueryInterface](/visual-cpp/atl/queryinterface) auf jeder [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Schnittstelle aufrufen [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) zum Abrufen einer Schnittstelle\).  
  
-   Generieren Sie eine Liste von DES, die jedem Programm im Prozess gedebuggt werden kann \(mithilfe [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)\).  
  
-   Wenden Sie Bearbeiten und Fortfahren Aktualisierungen \(Anlage\) in jedem Programm fortgesetzt \(durch Aufrufen von IDebugProcess2::EnumPrograms aufrufen und dann [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)\).  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
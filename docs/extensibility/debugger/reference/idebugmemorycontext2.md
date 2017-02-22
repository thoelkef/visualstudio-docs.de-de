---
title: "IDebugMemoryContext2 | Microsoft Docs"
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
  - "IDebugMemoryContext2"
helpviewer_keywords: 
  - "IDebugMemoryContext2-Schnittstelle"
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt eine Position im Adressbereich des Computers Ausführen des Programms, das gedebuggt wird.  
  
## Syntax  
  
```  
IDebugMemoryContext2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um eine Adresse im Speicher darzustellen.  
  
## Hinweise für Aufrufer  
 Ein Aufruf von [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) oder [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) gibt diese Schnittstelle zurück.  Außerdem Aufrufe von neuen RückholKopien [Hinzufügen](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) und [Subtrahieren](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) dieser Schnittstelle nach der geeigneten arithmetischen Operation ist angewendet wurden.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugMemoryContext2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Ruft den Benutzer angezeigten Namen für diesen Kontext ab.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Ruft Informationen ab, die den Kontext beschreibt.|  
|[Hinzufügen](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Fügt einen angegebenen Wert der aktuellen Adresse des Kontexts hinzu, um einen neuen Kontext zu erstellen.|  
|[Subtrahieren](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Subtrahiert einen angegebenen Wert aus der aktuellen Adresse des Kontexts, um einen neuen Kontext zu erstellen.|  
|[Vergleichen](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Vergleicht zwei Umgebungen, die sich in der Art von Vergleich angegebenen Flags.|  
  
## Hinweise  
 **Arbeitsspeicher** Fenster von Visual Studio wird angezeigt [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) zum Abrufen der `IDebugMemoryContext2`\-Schnittstelle, die den ausgewerteten Ausdruck enthält, der für die Speicheradresse verwendet wird.  Dieser Kontext wird anschließend an [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) und [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) übergeben, um die Adresse anzugeben, um zu lesen oder zu schreiben.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)   
 [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)   
 [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)   
 [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
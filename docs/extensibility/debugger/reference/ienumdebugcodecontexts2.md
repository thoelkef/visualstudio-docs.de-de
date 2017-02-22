---
title: "IEnumDebugCodeContexts2 | Microsoft Docs"
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
  - "IEnumDebugCodeContexts2"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2"
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugCodeContexts2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle listet die Code kontexte auf, die mit der Debugsitzung oder mit einem bestimmten Programm oder einem Dokument zugeordnet werden.  
  
## Syntax  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um eine Liste von Code kontexten für eine bestimmte Textposition in einem Programm oder eine Liste von Code kontexten für einen bestimmten Dokumentenkontext darstellt.  
  
## Hinweise für Aufrufer  
 Rufen Sie zum Abrufen [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) diese Schnittstelle, die eine Liste von Code kontexten für eine bestimmte Textposition im Quelldokument eines Programms darstellt.  
  
 Rufen Sie [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) an, die zum Abrufen dieser Schnittstelle, die eine Liste aller Code kontexte in einem bestimmten Quelldokument darstellt.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IEnumDebugCodeContexts2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Weiter](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Ruft eine angegebene Anzahl von Code kontexte in der Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Überspringt eine angegebene Anzahl von Code in einer kontexte Enumerationsfolge.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[Klonen](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Ruft die Anzahl der Code kontexten in einem Enumerator ab.|  
  
## Hinweise  
 Visual Studio ruft [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) auf, um eine Liste von Code kontexten aufzufüllen, die der Benutzer auswählen kann, wenn er die folgende Anweisung festlegen oder die Disassembly für eine Quelldatei anzeigt.  Mehrere Code kontexte können auftreten, z. B. wenn mehrere Instanzen einer Vorlage in \+\+\-style vorhanden ist.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
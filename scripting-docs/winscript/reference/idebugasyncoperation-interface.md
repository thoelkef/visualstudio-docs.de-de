---
title: "IDebugAsyncOperation-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugAsyncOperation-Schnittstelle"
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAsyncOperation-Schnittstelle
Der Prozessdebug\-Manager `IDebugAsyncOperation` implementiert die Schnittstelle.  Ein Sprachmodul ruft die `IDebugApplication::CreateAsyncDebugOperation`\-Methode auf, um ein Verweis auf diese Schnittstelle.  Das Sprachmodul kann die `IDebugAsyncOperation`\-Schnittstelle verwenden, um asynchrone Zugriff auf einen synchronen Debugvorgang zu ermöglichen.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugAsyncOperation`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Gibt den synchronen Debugvorgang zurück, der diesem Objekt zugeordnet ist.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Veranlasst den asynchronen Operation zu starten.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Bricht einen Vorgang ab.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Bestimmt, ob der Debugvorgang abgeschlossen ist.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Stellt den Rückgabewert bereit und gibt Objektparameter im synchronen Debugvorgang zurück.|
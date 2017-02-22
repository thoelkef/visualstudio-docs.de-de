---
title: "SccBeginBatch-Funktion | Microsoft Docs"
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
  - "SccBeginBatch"
helpviewer_keywords: 
  - "SccBeginBatch-Funktion"
ms.assetid: 33968183-2e15-4e0d-955b-ca12212d1c25
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# SccBeginBatch-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion startet eine Batch\-Sequenz von Quellcodeverwaltungsvorgänge. Die [SccEndBatch](../extensibility/sccendbatch-function.md) wird aufgerufen, um den Batch beenden. Diese Batches können nicht geschachtelt werden.  
  
## Syntax  
  
```cpp#  
SCCRTN SccBeginBatch(void);  
```  
  
#### Parameter  
 Keine.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Batch Vorgänge wurde erfolgreich gestartet.|  
|SCC\_E\_UNKNOWNERROR|Nicht spezifischen Fehler.|  
  
## Hinweise  
 Source Control Batches werden verwendet, um die gleichen Vorgänge über mehrere Projekte oder mehrere Kontexte auszuführen. Batches können verwendet werden, um redundante pro Projekt\-Dialogfelder über die Benutzeroberfläche während eines Vorgangs im Batch zu entfernen. Die `SccBeginBatch` \-Funktion und die [SccEndBatch](../extensibility/sccendbatch-function.md) werden als Funktionspaar verwendet, um Anfang und Ende eines Vorgangs anzugeben. Sie können geschachtelt, sein.`SccBeginBatch` Legt ein Flag, das angibt, dass ein Batchvorgang ausgeführt wird.  
  
 Während ein Batchvorgangs aktiviert ist, sollte das Quellcodeverwaltungs\-Plug\-in höchstens ein Dialogfeld für jede Frage dem Benutzer angezeigt und die Antwort über dieses Dialogfeld alle nachfolgenden Operationen angewendet.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccEndBatch](../extensibility/sccendbatch-function.md)
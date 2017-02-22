---
title: "SccEndBatch-Funktion | Microsoft Docs"
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
  - "SccEndBatch"
helpviewer_keywords: 
  - "SccEndBatch-Funktion"
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# SccEndBatch-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Funktion ist einen Batch von Quellcodeverwaltungsvorgänge beendet. Diese Batches können nicht geschachtelt werden.  
  
## Syntax  
  
```cpp#  
SCCRTN SccEndBatch(void);  
```  
  
#### Parameter  
 Keine.  
  
## Rückgabewert  
 Datenquellen\-Steuerelement Plug\-in\-Implementierung dieser Funktion muss einen der folgenden Werte zurückgeben:  
  
|Wert|Beschreibung|  
|----------|------------------|  
|SCC\_OK|Der Batch Vorgänge erfolgreich abgeschlossen.|  
|SCC\_E\_UNKNOWNERROR|Nicht spezifischen Fehler.|  
  
## Hinweise  
 Source Control Batches werden zum gleichen Quellcodeverwaltungsvorgänge über mehrere Projekte oder mehrere Kontexte auszuführen. Batches können verwendet werden, um redundante Dialogfelder über die Benutzeroberfläche während eines Vorgangs im Batch zu entfernen. Die [SccBeginBatch](../extensibility/sccbeginbatch-function.md) und die `SccEndBatch` Funktion werden als Paar verwendet, um Anfang und Ende eines Vorgangs anzugeben. Sie können geschachtelt, sein.  
  
## Siehe auch  
 [Source Control\-Plug\-in\-API\-Funktionen](../extensibility/source-control-plug-in-api-functions.md)   
 [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
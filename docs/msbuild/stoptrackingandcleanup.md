---
title: "StopTrackingAndCleanup | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "StopTrackingAndCleanup"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StopTrackingAndCleanup"
ms.assetid: 9f8c5994-2dfc-43c3-a5fb-89b2f8990429
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# StopTrackingAndCleanup
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beendet alle Nachverfolgung und gibt den von der Nachverfolgungssitzung verwendeten Arbeitsspeicher frei.  
  
## Syntax  
  
```  
HRESULT WINAPI StopTrackingAndCleanup(void);  
```  
  
## Rückgabewert  
 Gibt ein [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True)\-Element mit dem [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True)\-Bitsatz zurück, wenn die Nachverfolgung angehalten wurde.  
  
## Anforderungen  
 **Kopfzeile:** FileTracker.h  
  
## Siehe auch  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
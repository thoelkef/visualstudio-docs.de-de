---
title: "EndTrackingContext | Microsoft Docs"
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
  - "EndTrackingContext"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "EndTrackingContext"
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# EndTrackingContext
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beenden Sie den aktuellen Nachverfolgungskontext.  
  
## Syntax  
  
```  
HRESULT WINAPI EndTrackingContext();  
```  
  
## Rückgabewert  
 Ein [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) mit dem [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True)\-Bitsatz, wenn der Nachverfolgungskontext beendet wurde.  
  
## Anforderungen  
 **Kopfzeile:** FileTracker.h  
  
## Siehe auch  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
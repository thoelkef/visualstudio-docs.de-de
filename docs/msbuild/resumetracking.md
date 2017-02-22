---
title: "ResumeTracking | Microsoft Docs"
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
  - "ResumeTracking"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "ResumeTracking"
ms.assetid: d637e019-7c50-4b0a-812e-bc822001e697
caps.latest.revision: 4
caps.handback.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ResumeTracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Setzt die Nachverfolgung im aktuellen Kontext fort.  
  
## Syntax  
  
```  
HRESULT WINAPI ResumeTracking();  
```  
  
## Rückgabewert  
 Ein [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) mit dem [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True)\-Bitsatz, wenn die Nachverfolgung fortgesetzt wurde.  [E\_FAIL](assetId:///E_FAIL?qualifyHint=False&autoUpgrade=True) wird zurückgegeben, wenn die Nachverfolgung nicht fortgesetzt werden kann, da der Kontext nicht verfügbar war.  
  
## Anforderungen  
 **Kopfzeile:** FileTracker.h  
  
## Siehe auch  
 [SuspendTracking](../msbuild/suspendtracking.md)
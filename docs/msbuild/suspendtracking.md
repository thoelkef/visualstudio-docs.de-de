---
title: "SuspendTracking | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "SuspendTracking"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "SuspendTracking"
ms.assetid: f5e06e5a-8083-444c-99c1-07ba834226b5
caps.latest.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 3
---
# SuspendTracking
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Setzt die Nachverfolgung im aktuellen Kontext aus.  
  
## Syntax  
  
```  
HRESULT WINAPI SuspendTracking(void);  
```  
  
## Rückgabewert  
 Ein [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True)\-Element mit dem [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True)\-Bitsatz, wenn die Nachverfolgung ausgesetzt wurde.  
  
## Anforderungen  
 **Kopfzeile:** FileTracker.h  
  
## Siehe auch  
 [ResumeTracking](../msbuild/resumetracking.md)
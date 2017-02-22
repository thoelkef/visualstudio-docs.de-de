---
title: "StartTrackingContextWithRoot | Microsoft Docs"
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
  - "StartTrackingContextWithRoot"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContextWithRoot"
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Startet einen Nachverfolgungskontext unter Verwendung einer Antwortdatei, die einen Stammmarker angibt.  
  
## Syntax  
  
```  
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### Parameter  
 \[in\] `intermediateDirectory`  
 Das Verzeichnis, in dem das Nachverfolgungsprotokoll gespeichert werden soll.  
  
 \[in\] `taskName`  
 Identifiziert den Nachverfolgungskontext.  Dieser Name wird verwendet, um den Protokolldateinamen zu erstellen.  
  
 \[in\] `rootMarkerResponseFile`  
 Der Pfadname einer Antwortdatei, die einen Stammmarker enthält.  Der Stammname wird verwendet, um die gesamte Nachverfolgung für einen Kontext zusammen zu gruppieren.  
  
## Rückgabewert  
 Ein [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) mit dem [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True)\-Bitsatz, wenn der Nachverfolgungskontext erstellt wurde.  
  
## Anforderungen  
 **Kopfzeile:** FileTracker.h  
  
## Siehe auch  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
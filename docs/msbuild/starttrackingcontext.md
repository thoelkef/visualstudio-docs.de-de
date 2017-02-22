---
title: "StartTrackingContext | Microsoft Docs"
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
  - "StartTrackingContext"
apilocation: 
  - "filetracker.dll"
apitype: "COM"
helpviewer_keywords: 
  - "StartTrackingContext"
ms.assetid: 720cd295-38e7-4974-86db-b8106b1207ba
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# StartTrackingContext
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Starten Sie einen Nachverfolgungskontext.  
  
## Syntax  
  
```  
HRESULT WINAPI StartTrackingContext(LPCTSTR intermediateDirectory, LPCTSTR taskName);  
```  
  
#### Parameter  
 \[in\] `intermediateDirectory`  
 Das Verzeichnis, in dem das Nachverfolgungsprotokoll gespeichert werden soll.  
  
 \[in\] `taskName`  
 Identifiziert den Nachverfolgungskontext.  Dieser Name wird verwendet, um den Protokolldateinamen zu erstellen.  
  
## Rückgabewert  
 Ein [HRESULT](assetId:///HRESULT?qualifyHint=False&autoUpgrade=True) mit dem [SUCCEEDED](assetId:///SUCCEEDED?qualifyHint=False&autoUpgrade=True)\-Bitsatz, wenn der Nachverfolgungskontext erstellt wurde.  
  
## Anforderungen  
 **Kopfzeile:** FileTracker.h
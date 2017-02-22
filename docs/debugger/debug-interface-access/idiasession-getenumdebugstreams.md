---
title: "IDiaSession::getEnumDebugStreams | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession::getEnumDebugStreams-Methode"
ms.assetid: d294954b-80e9-476c-b9f0-5ca6fd575f68
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::getEnumDebugStreams
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine aufgelistete Sequenz Debuggen von Streams ab.  
  
## Syntax  
  
```cpp#  
HRESULT getEnumDebugStreams (   
   IDiaEnumDebugStreams** ppEnumDebugStreams  
)  
```  
  
#### Parameter  
 `ppEnumDebugStreams`  
 \[out\]  Gibt ein [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)\-Objekt zurück, das eine Liste von Debuggen von Streams enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)
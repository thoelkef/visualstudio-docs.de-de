---
title: "IDiaSession::findFileById | Microsoft Docs"
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
  - "IDiaSession::findFileById-Methode"
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findFileById
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft eine Quelldatei nach Bezeichner der Quelldatei ab oder legt diese fest.  
  
## Syntax  
  
```cpp#  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### Parameter  
 `uniqueId`  
 \[in\]  Gibt den Bezeichner der Quelldatei an.  
  
 `ppResult`  
 \[out\]  Gibt ein [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)\-Objekt zurück, das die abgerufene Quelldatei darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Bezeichner der Quelldatei ist ein eindeutiger Wert, der intern zum DIA SDK verwendet wird, um alle Quelldateien eindeutig zu erstellen.  Diese Methode wird i. d. R. an das intern DIA SDK verwendet.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
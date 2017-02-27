---
title: "IDiaSession::get_loadAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession::get_loadAddress-Methode"
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSession::get_loadAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Ladeadresse der ausführbaren Datei ab, die den Symbolen in diesem Symbolspeicher entspricht.  
  
## Syntax  
  
```cpp#  
HRESULT get_loadAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt eine virtuelle Adresse \(VA\), in der eine EXE\-Datei oder DLL\-Datei geladen wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die zurückgegebene Ladeadresse ist immer Nullen, es sei denn, speziell mit den [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)\-Methode festgelegt.  
  
## Siehe auch  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)
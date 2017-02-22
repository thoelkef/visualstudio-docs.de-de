---
title: "IDiaAddressMap::get_addressMapEnabled | Microsoft Docs"
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
  - "IDiaAddressMap::get_addressMapEnabled-Methode"
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::get_addressMapEnabled
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt an, ob eine Adressumsetzung für eine bestimmte Sitzung eingerichtet wurde.  
  
## Syntax  
  
```cpp#  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### Parameter  
 pRetVal  
 \[out\]  Gibt `TRUE` zurück, wenn die Adressabbildung aktiviert ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ausführbare aktualisieren Postprozessoren manchmal die ausführbare Datei.  Durchmesser enthält einen Mechanismus bereit, um die Übersetzung von Symbolen in das neue Lay\-out zu unterstützen.  
  
 Clientanwendungen können die Adressumsetzung für eine bestimmte Sitzung festlegen, indem sie die [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)\-Schnittstelle aus der [IDiaSession](../../debugger/debug-interface-access/idiasession.md)\-Schnittstelle abrufen und die [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)\-Methode gefolgt von einem Aufruf der [IDiaAddressMap::put\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)\-Methode aufrufen.  Die `get_addressMapEnabled`\-Methode gibt die Ergebnisse eines Aufrufs der `put_addressMapEnabled`\-Methode zurück.  
  
## Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)
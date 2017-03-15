---
title: "IDiaAddressMap::put_addressMapEnabled | Microsoft Docs"
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
  - "IDiaAddressMap::put_addressMapEnabled-Methode"
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gibt an, ob die Adressumsetzung verwendet werden soll, um Symbol adressen zu übersetzen.  
  
## Syntax  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### Parameter  
 NewVal  
 \[in\]  Auf `TRUE` , um die Übersetzung der Symbole zu aktivieren oder zu deaktivieren, um `FALSE` .  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ausführbare aktualisieren Postprozessoren manchmal die ausführbare Datei.  Durchmesser enthält einen Mechanismus bereit, um die Übersetzung von Symbolen in das neue Lay\-out zu unterstützen.  
  
 Wenn eine PDB\-Datei geladen wird, wird die Adressumsetzung, die in der Datei gespeichert wird, können.  Es gibt jedoch Situationen, wenn eine Clientanwendung möglicherweise eigene Adressumsetzung angeben muss, indem sie die [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)\-Methode aufruft.  Wenn die `set_addressMap`\-Methode erfolgreich ist, muss die Clientanwendung die `put_addressMapEnabled`\-Methode mit einem Parameter von `NewVal``TRUE` aufrufen, um die Verwendung dieser Adressumsetzung zu aktivieren.  
  
 Der aktuelle Status der Adressumsetzung aktiviert ist, kann durch einen Aufruf der [IDiaAddressMap::get\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)\-Methode abgerufen werden.  
  
## Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)
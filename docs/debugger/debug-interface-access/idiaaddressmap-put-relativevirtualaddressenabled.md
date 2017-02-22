---
title: "IDiaAddressMap::put_relativeVirtualAddressEnabled | Microsoft Docs"
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
  - "IDiaAddressMap::put_relativeVirtualAddressEnabled-Methode"
ms.assetid: 767c078e-8ad7-4940-9e00-cae7704aadee
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::put_relativeVirtualAddressEnabled
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ermöglicht dem Client, um die Berechnung und Verwendung von relativen virtuellen Adressen \(RVA\) zu aktivieren oder zu deaktivieren.  
  
## Syntax  
  
```cpp#  
HRESULT put_relativeVirtualAddressEnabled (   
   BOOL NewVal  
);  
```  
  
#### Parameter  
 NewVal  
 \[in\]  Auf `TRUE` zu aktivieren oder zu deaktivieren `FALSE` .  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Adressen für die Debug\- Objekte, die von Durchmesser\-Schnittstellen und Bild relativ zur Seite der ausführbaren Datei beschrieben werden, können als relative virtuelle Adressen abgerufen werden.  
  
 Die Verwendung von RVAs wird aktiviert, wenn zuerst Segmente aus einer PDB\-Datei geladen werden.  Um den aktuellen Zustand der Verwendung von RVAs abzurufen, rufen Sie die [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)\-Methode auf.  
  
 Die `put_relativeVirtualAddress`\-Methode muss aufgerufen werden, um die RVAs zu ermöglichen, nachdem ein erfolgreicher Aufruf der [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md) Header des Bilds neue Methode verfügt. eingerichteten  
  
## Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)
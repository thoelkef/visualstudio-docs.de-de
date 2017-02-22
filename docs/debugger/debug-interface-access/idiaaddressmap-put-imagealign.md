---
title: "IDiaAddressMap::put_imageAlign | Microsoft Docs"
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
  - "IDiaAddressMap::put_imageAlign-Methode"
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legt die Ausrichtung des Bilds fest.  
  
## Syntax  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### Parameter  
 NewVal  
 \[in\]  Der neue Wert für das Bild für die ausführbare Datei.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Bilder \(geladene ausführbare Dateien\) sind mit den angegebenen Arbeitsspeicher begrenzen ausgerichtet.  Diese Ausrichtung kann beeinträchtigt sein von der aktuellen Systemarchitektur und zu kompilieren und die Verknüpfungszeit. Optionen  Bild Ausrichtung ist immer ein Byte begrenzen.  Die folgenden Bild für Werte sind gültig: 1, 2, 4, 8, 16, 32 und 64 Byte begrenzen.  
  
 Die aktuelle Bild kann mit Ausrichtung von einem Aufruf der [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)\-Methode abgerufen werden.  
  
> [!NOTE]
>  Das Bild wird bereits geladen, bis diese Methode aufgerufen werden kann.  Die `put_imageAlign`\-Methode wird in der Regel verwendet, wenn das Bild verschoben oder geändert wurde und eine neue Ausrichtung erforderlich ist.  
  
## Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
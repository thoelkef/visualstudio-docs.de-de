---
title: "IDiaAddressMap::set_imageHeaders | Microsoft Docs"
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
  - "IDiaAddressMap::set_imageHeaders-Methode"
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Legt Header des Bilds fest, um relative virtuelle Adressenumwandlung zu aktivieren.  
  
## Syntax  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### Parameter  
 cbData  
 \[in\]  Anzahl von Bytes Headerdaten.  Muss `n*sizeof(IMAGE_SECTION_HEADER)` , wo die Anzahl der `n` Kapitelüberschriften in der ausführbaren Datei.  
  
 Daten \[\]  
 \[in\]  Ein Array als Bild `IMAGE_SECTION_HEADER` Strukturen Header verwendet werden soll.  
  
 originalHeaders  
 \[in\]  Auf `FALSE` , wenn das Bild vom neuen Header Bild, `TRUE` , wenn sie das Originalbild vor dem Upgrade entsprechen.  In der Regel ist dies zu `TRUE` nur in Kombination mit Aufrufen der [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)\-Methode festgelegt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die `IMAGE_SECTION_HEADER` Struktur wird in Winnt.h deklariert und das angegebene Bild kapitelüberschrift Format der ausführbaren Datei darstellt.  
  
 Relative virtuelle câdressenberechnungen hängen die nach dem `IMAGE_SECTION_HEADER`\-Werten ab.  Normalerweise ruft der Durchmesser diese von der Programmdatenbankdatei \(.pdb\) ab.  Wenn diese Werte fehlen, ist der Durchmesser keine relative virtuelle Adressen zu berechnen und die [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)\-Methode gibt `FALSE`zurück.  Nach der Bereitstellung der fehlenden Header Bild aus dem Bild selbst muss der Client die [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)\-Methode aufrufen, um die relativen virtuellen câdressenberechnungen zu aktivieren.  
  
## Siehe auch  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)
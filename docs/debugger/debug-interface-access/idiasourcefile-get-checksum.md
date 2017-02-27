---
title: "IDiaSourceFile::get_checksum | Microsoft Docs"
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
  - "IDiaSourceFile::get_checksum-Methode"
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Prüfsummen Bytes ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Parameter  
 `cbData`  
 \[in\]  Größe in Bytes im Datenpuffer.  
  
 `pcbData`  
 \[out\]  Prüfsummen Gibt die Anzahl von Bytes zurück.  Dieser Parameter darf nicht `NULL` sein.  
  
 `data`  
 \[in, out\]  Ein Puffer, der mit den Bytes Prüfsummen ausgefüllt wird.  Wenn dieser Parameter `NULL`ist, gibt `pcbData` die Anzahl von Bytes erforderlich zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Um den Typ des Prüfsummenalgorithmus zu bestimmen, der verwendet wurde, um die Prüfsummen Bytes zu generieren, rufen Sie die [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)\-Methode auf.  
  
 Die Prüfsumme wird in der Regel vom Bild der Quelldatei generiert, daher werden Änderungen in der Quelldatei in den Änderungen in Bytes Prüfsummen wiedergibt.  Wenn die Prüfsummen übereinstimmen, die keine Prüfsumme Bytes aus dem geladenen Bild der Datei generiert wird, sollte die Datei beschädigt oder als manipuliert werden.  
  
 Typische Prüfsummen sind niemals mehr als 32 Bytes wird jedoch Größe nehmen nicht an, das die maximale Größe einer Prüfsumme ist.  Legen Sie den `data`\-Parameter in `NULL` fest, um die erforderliche Anzahl von Bytes abgerufen, um die Prüfsumme abzurufen.  Anschließend weisen Sie einen entsprechenden Puffer der Größe, und rufen Sie die Methode erneut mit dem neuen Puffer an.  
  
## Siehe auch  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)
---
title: "IDiaSourceFile::get_uniqueId | Microsoft Docs"
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
  - "IDiaSourceFile::get_uniqueId-Methode"
ms.assetid: e0b8dbc0-6061-4f31-bead-2cd72be44e41
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSourceFile::get_uniqueId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft einen einfachen ganzzahligen Schlüsselwert ab, der für das Bild eindeutig ist.  
  
## Syntax  
  
```cpp#  
HRESULT get_uniqueId (   
   DWORD* pRetVal  
);  
```  
  
#### Parameter  
 `pRetVal`  
 \[out\]  Gibt einen einfachen ganzzahligen Schlüsselwert zurück, der für das Bild eindeutig ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Das Vergleichen von Schlüsseln anstelle von Zeichenfolgen kann das Verarbeiten von Zeilennummern beschleunigen.  
  
## Siehe auch  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
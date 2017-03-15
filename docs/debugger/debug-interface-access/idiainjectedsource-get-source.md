---
title: "IDiaInjectedSource::get_source | Microsoft Docs"
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
  - "IDiaInjectedSource::get_source-Methode"
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaInjectedSource::get_source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft die Bytes ab.  
  
## Syntax  
  
```cpp#  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Parameter  
 `cbData`  
 \[in\]  Die Anzahl der Bytes, die die Größe des Datenpuffers darstellt.  
  
 `pcbData`  
 \[out\]  Gibt die Anzahl von Bytes zurück, die die Bytes zurückgegeben.  Wenn `data``NULL`ist, ist `pcbData` die Gesamtzahl von Bytes verfügbaren Daten.  
  
 `data[]`  
 \[out\]  Ein Puffer, der mit den Bytes Quelle aufgefüllt werden soll.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn diese Eigenschaft nicht unterstützt wird.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
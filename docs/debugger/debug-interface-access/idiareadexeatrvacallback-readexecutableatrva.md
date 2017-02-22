---
title: "IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs"
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
  - "IDiaReadExeAtRVACallback::ReadExecutableAtRVA-Methode"
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Liest die angegebene Anzahl von Bytes, die an der angegebenen relativen virtuellen Adresse \(RVA\) beginnen mit der ausführbaren Datei.  
  
## Syntax  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Parameter  
 `relativeVirtualAddress`  
 \[in\]  Die RVA in die ausführbare Datei, an dem der Lesevorgang beginnen soll.  
  
 `cbData`  
 \[in\]  Die Anzahl der zu lesenden Bytes.  
  
 `pcbData`  
 \[out\]  Gibt die Anzahl der gelesenen Bytes zurück.  
  
 `data[]`  
 \[in, out\]  Ein Array von Bytes, das ausgefüllt wird, aus der Datei gelesen.  
  
## Hinweise  
 Diese Methode wird vom Code aufgerufen, um die Durchmesser\-Stütz Bytes aus einer ausführbaren Datei mit einer relativen virtuellen Adresse zu laden.  Diese Methode wird zur Unterstützung der [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)\-Methode aufgerufen.  
  
## Siehe auch  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
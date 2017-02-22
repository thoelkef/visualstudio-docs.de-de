---
title: "IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs"
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
  - "IDiaReadExeAtOffsetCallback::ReadExecutableAt-Methode"
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Liest die angegebene Anzahl von Bytes, die am angegebenen Offset aus einer ausführbaren Datei starten.  
  
## Syntax  
  
```cpp#  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### Parameter  
 fileOffset  
 \[in\]  Der Offset in die ausführbare Datei, an dem der Lesevorgang beginnen soll.  
  
 cbData  
 \[in\]  Die Anzahl der zu lesenden Bytes.  
  
 pcbData  
 \[out\]  Gibt die Anzahl der gelesenen Bytes zurück.  
  
 Daten \[\]  
 \[in, out\]  Ein Array, das die Bytes der Datei gelesen gefüllt wird.  
  
## Hinweise  
 Diese Methode wird vom Code aufgerufen, um die Durchmesser\-Stütz Bytes aus einer ausführbaren Datei mithilfe eines Offsets der absoluten Datei zu laden.  Diese Methode wird zur Unterstützung der [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)\-Methode aufgerufen.  
  
## Siehe auch  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
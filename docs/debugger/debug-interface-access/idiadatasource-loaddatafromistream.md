---
title: "IDiaDataSource::loadDataFromIStream | Microsoft Docs"
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
  - "IDiaDataSource::loadDataFromIStream-Methode"
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaDataSource::loadDataFromIStream
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Bereitet die Debugdaten vor, die in einer gespeicherten Programmdatenbankdatei \(.pdb\), die durch einen Stream im Speicher zugegriffen wird.  
  
## Syntax  
  
```cpp#  
HRESULT loadDataFromIStream (   
   IStream* pIStream  
);  
```  
  
#### Parameter  
 pIStream  
 \[in\]  Ein <xref:IStream>\-Objekt, das den Stream zur Verwendung darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  In der folgenden Tabelle werden die möglichen Rückgabewerte für diese Methode auf.  
  
|Wert|Beschreibung|  
|----------|------------------|  
|E\_PDB\_FORMAT|Versucht, eine Datei mit einem veralteten Format zuzugreifen.|  
|E\_INVALIDARG|Invalidparameter.|  
|E\_UNEXPECTED|Datenquelle ist bereits vorbereitet wurde.|  
  
## Hinweise  
 Mit dieser Methode können die Debugdaten aus dem Arbeitsspeicher auf eine ausführbare Datei abgerufen werden, durch ein <xref:IStream>\-Objekt.  
  
 Um eine PDB\-Datei ohne Validierung zu laden, verwenden Sie die [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)\-Methode.  
  
 Um die PDB\-Datei mit bestimmten Kriterien zu überprüfen, verwenden Sie die [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)\-Methode.  
  
 Um zum ladevorgang Daten zugreifen zu können \(durch einen Rückrufmechanismus\), verwenden Sie die [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)\-Methode.  
  
## Siehe auch  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
---
title: "IDiaDataSource::loadDataFromPdb | Microsoft Docs"
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
  - "IDiaDataSource::loadDataFromPdb-Methode"
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::loadDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Öffnet und bereitet eine Programmdatenbankdatei \(.pdb\) als Debugsymbolinformationen auf Datenquelle.  
  
## Syntax  
  
```cpp#  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### Parameter  
 pdbPath  
 \[in\]  Der Pfad zur PDB\-Datei.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  In der folgenden Tabelle werden die möglichen Rückgabewerte für diese Methode auf.  
  
|Wert|Beschreibung|  
|----------|------------------|  
|E\_PDB\_NOT\_FOUND|Fehlgeschlagene die Datei öffnen oder bestimmt, dass die Datei ein ungültiges Format aufweist.|  
|E\_PDB\_FORMAT|Versucht, eine Datei mit einem veralteten Format zuzugreifen.|  
|E\_INVALIDARG|Ungültiger Parameter.|  
|E\_UNEXPECTED|Datenquelle ist bereits vorbereitet wurde.|  
  
## Hinweise  
 Diese Methode lädt die Debugdaten direkt von einer PDB\-Datei.  
  
 Um die PDB\-Datei mit bestimmten Kriterien zu überprüfen, verwenden Sie die [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)\-Methode.  
  
 Um zum ladevorgang Daten zugreifen zu können \(durch einen Rückrufmechanismus\), verwenden Sie die [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)\-Methode.  
  
 Um eine PDB\-Datei direkt aus dem Arbeitsspeicher zu laden, verwenden Sie die [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)\-Methode.  
  
## Beispiel  
  
```cpp#  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## Siehe auch  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
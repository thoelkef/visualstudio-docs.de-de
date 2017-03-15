---
title: "IDiaDataSource | Microsoft Docs"
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
  - "IDiaDataSource-Schnittstelle"
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IDiaDataSource
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Initiiert den Zugriff auf eine Quelle von Debugsymbolen.  
  
## Syntax  
  
```  
IDiaDataSource : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaDataSource`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaDataSource::get\_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Ruft den Dateinamen für den letzten Ladefehler ab.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Öffnet und bereitet eine Programmdatenbankdatei \(.pdb\) als Debugsymbolinformationen auf Datenquelle.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Öffnet auf und überprüft, ob die Programmdatenbankdatei \(.pdb\) die jeweiligen Signaturinformationen übereinstimmt. bereitet die PDB\-Datei als die Datenquelle vor.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Öffnet und bereitet die Debugdaten vor, die mit der .exe\-\/.dll Datei zugeordnet sind.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Bereitet die Debugdaten vor, die in einer gespeicherten Programmdatenbankdatei \(.pdb\), die durch einen Stream im Speicher zugegriffen wird.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Öffnet eine Sitzung zum Abfragen von Symbolen.|  
  
## Hinweise  
 Ein Aufruf an eine der Lademethoden der `IDiaDataSource`\-Schnittstelle öffnet die Quelle des Symbols.  Ein erfolgreicher Aufruf der [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)\-Methode gibt eine [IDiaSession](../../debugger/debug-interface-access/idiasession.md)\-Schnittstelle zurück, die das Abfragen der Datenquelle unterstützt.  Wenn die Lademethode dateibezogenen einen Fehler zurückgibt, enthält der Rückgabewert der Methode [IDiaDataSource::get\_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) den Dateinamen, der dem Fehler zugeordnet ist.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird abgerufen, indem die `CoCreateInstance`\-Funktion mit den Klassenbezeichner `CLSID_DiaSource` und die Schnittstellen\-ID von `IID_IDiaDataSource`aufruft.  Im Beispiel wird gezeigt, wie diese Schnittstelle ermittelt wird.  
  
## Beispiel  
  
```cpp#  
  
      IDiaDataSource* pSource;  
HRESULT hr = CoCreateInstance(CLSID_DiaSource,  
                              NULL,  
                              CLSCTX_INPROC_SERVER,  
                              IID_IDiaDataSource,  
                              (void**) &pSource);  
if (FAILED(hr))  
{  
    // Report error and exit  
}  
```  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
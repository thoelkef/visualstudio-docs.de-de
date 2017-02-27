---
title: "IDiaDataSource::loadDataForExe | Microsoft Docs"
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
  - "IDiaDataSource::loadDataForExe-Methode"
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Öffnet und bereitet die Debugdaten vor, die mit der .exe\-\/.dll Datei zugeordnet sind.  
  
## Syntax  
  
```cpp#  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### Parameter  
 executable  
 \[in\]  Pfad zur EXE\-Datei oder DLL\-Datei.  
  
 searchPath  
 \[in\]  Alternative zum Debuggen von Daten zu durchsuchende Pfad.  
  
 pCallback  
 \[in\]  Eine `IUnknown`\-Schnittstelle für ein Objekt, das eine Rückrufschnittstelle, wie [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)und\/oder die [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)\-Schnittstellen unterstützt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  In der folgenden Tabelle werden einige der möglichen Fehlercodes für diese Methode auf.  
  
|Wert|Beschreibung|  
|----------|------------------|  
|E\_PDB\_NOT\_FOUND|Fehlgeschlagene, die Datei oder die Datei geöffnet hat ein ungültiges Format.|  
|E\_PDB\_FORMAT|Versucht, eine Datei mit einem veralteten Format zuzugreifen.|  
|E\_PDB\_INVALID\_SIG|Signatur stimmen nicht überein.|  
|E\_PDB\_INVALID\_AGE|Alter stimmen nicht überein.|  
|E\_INVALIDARG|Ungültiger Parameter.|  
|E\_UNEXPECTED|Datenquelle ist bereits vorbereitet wurde.|  
  
## Hinweise  
 Der von Dateinamen der zugeordnete Kopfzeile der .exe\-\/.dll Speicherort der Daten Debuggen.  
  
 Diese Methode liest den Debug\- und anschließend die Header sucht und bereitet die Debugdaten vor.  Der Status der Suche optional wird durch Rückrufe gemeldet werden, kann gesteuert.  Beispielsweise wird [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) aufgerufen, wenn die `IDiaDataSource::loadDataForExe`\-Methode eine Debug\- Verzeichnis durchsucht und die Verarbeitung ausführt.  
  
 Die [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) und [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)\-Schnittstellen ermöglichen die Clientanwendung alternative Methoden zum Lesen von Daten aus der ausführbaren Datei bereitzustellen, wenn die Datei nicht direkt vom Standardwert datei\-e\/a zugegriffen werden kann.  
  
 Um eine PDB\-Datei ohne Validierung zu laden, verwenden Sie die [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)\-Methode.  
  
 Um die PDB\-Datei mit bestimmten Kriterien zu überprüfen, verwenden Sie die [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)\-Methode.  
  
 Um eine PDB\-Datei direkt aus dem Arbeitsspeicher zu laden, verwenden Sie die [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)\-Methode.  
  
## Beispiel  
  
```cpp#  
class MyCallBack: public IDiaLoadCallback  
{  
...  
};  
MyCallBack callback;  
...  
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);  
if (FAILED(hr))  
{  
    // Report error  
}  
```  
  
## Siehe auch  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
---
title: "IDiaInjectedSource | Microsoft Docs"
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
  - "IDiaInjectedSource-Schnittstelle"
ms.assetid: 75192c5c-812d-4675-9dc5-4c2cff3ba503
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaInjectedSource
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Zugriffe eingefügter Quellcode in einer Durchmesser\-Datenquelle.  
  
## Syntax  
  
```  
IDiaInjectedSource : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaInjectedSource`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaInjectedSource::get\_crc](../../debugger/debug-interface-access/idiainjectedsource-get-crc.md)|Ruft eine zyklische Blockprüfung \(CRC\) berechnet der Bytes des Quellcodes ab.|  
|[IDiaInjectedSource::get\_length](../../debugger/debug-interface-access/idiainjectedsource-get-length.md)|Ruft die Anzahl von Bytes des Codes ab.|  
|[IDiaInjectedSource::get\_filename](../../debugger/debug-interface-access/idiainjectedsource-get-filename.md)|Ruft den Dateinamen für die Quelle ab.|  
|[IDiaInjectedSource::get\_objectFilename](../../debugger/debug-interface-access/idiainjectedsource-get-objectfilename.md)|Ruft den Namen der Protokolldatei Objekt ab, auf das die Quelle kompiliert wurde.|  
|[IDiaInjectedSource::get\_virtualFilename](../../debugger/debug-interface-access/idiainjectedsource-get-virtualfilename.md)|Ruft den Namen ab, der dem Nicht\-Datei\-Quellcode angegeben ist. d. h. Code, der eingefügt wurde.|  
|[IDiaInjectedSource::get\_sourceCompression](../../debugger/debug-interface-access/idiainjectedsource-get-sourcecompression.md)|Ruft den Zähler der verwendeten Sources komprimierung ab.|  
|[IDiaInjectedSource::get\_source](../../debugger/debug-interface-access/idiainjectedsource-get-source.md)|Ruft die Bytes ab.|  
  
## Hinweise  
 Eingefügte Quelle ist Text, der während der Kompilierung eingefügt wird.  Dies bedeutet nicht `#include` die Präprozessorausgabe in C\+\+ verwendet wird.  
  
## Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle, indem sie die [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md) oder [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)\-Methoden aufgerufen werden.  Zeigen Sie die [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)\-Schnittstelle als Beispiel für die `IDiaInjectedSource`\-Schnittstelle abzurufen.  
  
## Beispiel  
 Dieses Beispiel zeigt die Daten an, die von der `IDiaInjectedSource`\-Schnittstelle zur Verfügung stehen.  Für einen alternativen Ansatz mit der [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)\-Schnittstelle finden Sie im Beispiel in der [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)\-Schnittstelle.  
  
```cpp#  
void PrintInjectedSource(IDiaInjectedSource* pSource)  
{  
    ULONGLONG codeLength      = 0;  
    DWORD     crc             = 0;  
    DWORD     compressionType = 0;  
    BSTR      sourceFilename  = NULL;  
    BSTR      objectFilename  = NULL;  
    BSTR      virtualFilename = NULL;  
  
    std::cout << "Injected Source:" << std::endl;  
    if (pSource != NULL)  
    {  
        if (pSource->get_crc(&crc) == S_OK &&  
            pSource->get_sourceCompression(&compressionType) == S_OK &&  
            pSource->get_length(&codeLength) == S_OK)  
        {  
            wprintf(L"  crc = %lu\n", crc);  
            wprintf(L"  code length = %I64u\n",codeLength);  
            wprintf(L"  compression type code = %lu\n", compressionType);  
        }  
  
        wprintf(L"  source filename: ");  
        if (pSource->get_filename(&sourceFilename) == S_OK)  
        {  
            wprintf(L"%s", sourceFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  object filename: ");  
        if (pSource->get_filename(&objectFilename) == S_OK)  
        {  
            wprintf(L"%s", objectFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        wprintf(L"  virtual filename: ");  
        if (pSource->get_filename(&virtualFilename) == S_OK)  
        {  
            wprintf(L"%s", virtualFilename);  
        }  
        else  
        {  
            wprintf(L"<none>");  
        }  
        wprintf(L"\n");  
  
        SysFreeString(sourceFilename);  
        SysFreeString(objectFilename);  
        SysFreeString(virtualFilename);  
    }  
}  
```  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)   
 [IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
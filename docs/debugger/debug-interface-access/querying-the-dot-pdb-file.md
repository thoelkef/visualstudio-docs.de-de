---
title: Abfragen der. PDB-Datei | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b552300926ae0448aacd084b54934f03527f81e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31470061"
---
# <a name="querying-the-pdb-file"></a>Abfragen der PDB-Datei
Eine Programmdatenbankdatei (.pdb Erweiterung) ist eine Binärdatei, die Typ und symbolische Debuginformationen, die gesammelt wurden, im Verlauf des kompilieren und verknüpfen das Projekt enthält. Eine PDB-Datei wird erstellt, wenn Sie ein C/C++-Programm mit Kompilieren **/Zi** oder **/Zi** oder ein [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], oder [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] Programmieren mit der **/debug** -Option. Objektdateien enthalten Verweise in der PDB-Datei für Debuginformationen. Weitere Informationen zu Pdb-Dateien, finden Sie unter [PDB-Dateien](http://msdn.microsoft.com/en-us/1761c84e-8c2c-4632-9649-b5f99964ed3f). Eine DIA-Anwendung kann die folgenden allgemeinen Schritte verwenden, um ausführliche Informationen zu den verschiedenen Symbole, Objekten und Datenelemente innerhalb eines ausführbaren Images zu erhalten.  
  
### <a name="to-query-the-pdb-file"></a>Zum Abfragen der PDB-Datei  
  
1.  Abrufen eine Datenquelle durch das Erstellen einer [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) Schnittstelle.  
  
    ```C++  
    CComPtr<IDiaDataSource> pSource;  
    hr = CoCreateInstance( CLSID_DiaSource,  
                           NULL,  
                           CLSCTX_INPROC_SERVER,  
                           __uuidof( IDiaDataSource ),  
                          (void **) &pSource);  
  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    ```  
  
2.  Rufen Sie [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) oder [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) die Debuginformationen geladen.  
  
    ```C++  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    ```  
  
3.  Rufen Sie [idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) So öffnen ein [IDiaSession](../../debugger/debug-interface-access/idiasession.md) für den Zugriff auf die Debuginformationen.  
  
    ```C++  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  Verwenden Sie die Methoden in `IDiaSession` Abfrage für die Symbole in der Datenquelle.  
  
    ```C++  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  Verwenden der `IDiaEnum*` Schnittstellen aufgelistet, und Durchsuchen die Symbole oder andere Elemente an, Debuginformationen.  
  
    ```C++  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )  
    {  
         // Do something with each IDiaTable.  
    }  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
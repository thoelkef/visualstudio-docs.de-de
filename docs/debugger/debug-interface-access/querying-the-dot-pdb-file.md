---
title: Abfragen der. PDB-Datei | Microsoft-Dokumentation
ms.date: 11/04/2016
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
ms.openlocfilehash: 3f909067c704686be4608546cc891df7f131107e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53819549"
---
# <a name="querying-the-pdb-file"></a>Abfragen der PDB-Datei
Eine Programmdatenbankdatei (Dateierweiterung ".pdb") ist eine Binärdatei, die Art und symbolische Debuginformationen gesammelt, die im Verlauf des kompilieren und verknüpfen das Projekt enthält. Eine PDB-Datei wird erstellt, beim Kompilieren eines C/C++-Programms mit **"/ Zi"** oder **"/ Zi"** oder [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], oder [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] Programmierung mit der **/debug** -Option. Objektdateien enthalten Verweise in die PDB-Datei für Debuginformationen. Weitere Informationen zu Pdb-Dateien, finden Sie unter [PDB-Dateien](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100)). Eine DIA-Anwendung können die folgenden allgemeinen Schritte zum Abrufen von Details zu den verschiedenen Symbolen, Objekte und Datenelemente innerhalb von ein ausführbares Image.  
  
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
  
3.  Rufen Sie [idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) zum Öffnen einer [IDiaSession](../../debugger/debug-interface-access/idiasession.md) für den Zugriff auf die Debuginformationen.  
  
    ```C++  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  Verwenden Sie die Methoden `IDiaSession` Abfrage für die Symbole in der Datenquelle.  
  
    ```C++  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  Verwenden der `IDiaEnum*` Schnittstellen zum Auflisten und Durchsuchen die Symbole oder andere Elemente Debuginformationen.  
  
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
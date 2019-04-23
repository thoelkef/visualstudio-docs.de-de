---
title: Abfragen der. PDB-Datei | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3cb95da9bc6405d313aa32e208d68df4327db6f4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087897"
---
# <a name="querying-the-pdb-file"></a>Abfragen der PDB-Datei
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eine Programmdatenbankdatei (Dateierweiterung ".pdb") ist eine Binärdatei, die Art und symbolische Debuginformationen gesammelt, die im Verlauf des kompilieren und verknüpfen das Projekt enthält. Eine PDB-Datei wird erstellt, beim Kompilieren eines C/C++-Programms mit **"/ Zi"** oder **"/ Zi"** oder [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], oder [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] Programmierung mit der **/debug** -Option. Objektdateien enthalten Verweise in die PDB-Datei für Debuginformationen. Weitere Informationen zu Pdb-Dateien, finden Sie unter [PDB-Dateien](http://msdn.microsoft.com/1761c84e-8c2c-4632-9649-b5f99964ed3f). Eine DIA-Anwendung können die folgenden allgemeinen Schritte zum Abrufen von Details zu den verschiedenen Symbolen, Objekte und Datenelemente innerhalb von ein ausführbares Image.  
  
### <a name="to-query-the-pdb-file"></a>Zum Abfragen der PDB-Datei  
  
1. Abrufen eine Datenquelle durch das Erstellen einer [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) Schnittstelle.  
  
    ```cpp#  
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
  
2. Rufen Sie [idiadatasource:: Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) oder [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) die Debuginformationen geladen.  
  
    ```cpp#  
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
  
3. Rufen Sie [idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) zum Öffnen einer [IDiaSession](../../debugger/debug-interface-access/idiasession.md) für den Zugriff auf die Debuginformationen.  
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4. Verwenden Sie die Methoden `IDiaSession` Abfrage für die Symbole in der Datenquelle.  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5. Verwenden der `IDiaEnum*` Schnittstellen zum Auflisten und Durchsuchen die Symbole oder andere Elemente Debuginformationen.  
  
    ```cpp#  
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

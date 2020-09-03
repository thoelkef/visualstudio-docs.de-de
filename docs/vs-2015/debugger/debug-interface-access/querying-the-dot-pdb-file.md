---
title: Abfragen von. PDB-Datei | Microsoft-Dokumentation
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
ms.openlocfilehash: 9b9013d41ac4d5ca890e7cc9e09b5eb9415cb640
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691329"
---
# <a name="querying-the-pdb-file"></a>Abfragen der PDB-Datei
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bei einer Programm Datenbankdatei (Erweiterung. pdb) handelt es sich um eine Binärdatei, die Typen-und symbolische Debuginformationen enthält, die im Verlauf der Kompilierung und Verknüpfung des Projekts gesammelt werden. Eine PDB-Datei wird erstellt, wenn Sie ein C/C++-Programm mit **/Zi** oder **/Zi** oder einem [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Programm, oder [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] mit der **/Debug** -Option kompilieren. Objektdateien enthalten Verweise auf die PDB-Datei zum Debuggen von Informationen. Weitere Informationen zu PDB-Dateien finden Sie unter [PDB-Dateien](https://msdn.microsoft.com/1761c84e-8c2c-4632-9649-b5f99964ed3f). Eine Dia-Anwendung kann die folgenden allgemeinen Schritte zum Abrufen von Details über die verschiedenen Symbole, Objekte und Datenelemente innerhalb eines ausführbaren Images verwenden.  
  
### <a name="to-query-the-pdb-file"></a>So Fragen Sie die PDB-Datei ab  
  
1. Rufen Sie eine Datenquelle ab, indem Sie eine [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) -Schnittstelle erstellen.  
  
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
  
2. Nennen Sie [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) oder [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) , um die Debuginformationen zu laden.  
  
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
  
3. Aufrufen von [IDiaDataSource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) zum Öffnen einer [IDiaSession](../../debugger/debug-interface-access/idiasession.md) , um Zugriff auf die Debuginformationen zu erhalten.  
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4. Verwenden Sie die Methoden in `IDiaSession` , um die Symbole in der Datenquelle abzufragen.  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5. Verwenden `IDiaEnum*` Sie die-Schnittstellen, um die Symbole oder andere Elemente der Debuginformationen aufzulisten und zu durchsuchen.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)

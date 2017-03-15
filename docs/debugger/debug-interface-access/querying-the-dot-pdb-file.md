---
title: "Abfragen der PDB-Datei | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "PDB-Dateien"
  - "PDB-Dateien, Abfragen"
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Abfragen der PDB-Datei
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Eine Programmdatenbankdatei \(Erweiterung .pdb\) handelt es sich um eine Binärdatei, die den Typ und symbolischen Debuginformationen enthält, die im Verlauf des Kompilierens und des Verknüpfens des Projekts gesammelt werden.  Eine PDB\-Datei wird erstellt, wenn Sie mit **\/ZI** Ein Programm oder **\/Zi** \/C \+\+ oder [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]oder [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] Programm mit der **\/debug** Option kompilieren.  Objektdateien enthalten Verweise in die PDB\-Datei für Debuginformationen.  Weitere Informationen zu VEH\-Dateien finden Sie unter [PDB Files](http://msdn.microsoft.com/de-de/1761c84e-8c2c-4632-9649-b5f99964ed3f).  Eine Durchmesser\-Anwendung kann die folgenden allgemeinen Schritte ausführen, um ausführliche Informationen zu erhalten, die Symbole über die verschiedenen Objekte und die Datenelemente innerhalb eines ausführbaren Images.  
  
### Um die PDB\-Datei abfragen  
  
1.  Ruft eine Datenquelle ab, indem Sie eine [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)\-Schnittstelle erstellen.  
  
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
  
2.  Rufen Sie [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) oder [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) auf, um die Debuginformationen zu laden.  
  
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
  
3.  Rufen Sie [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) auf, um [IDiaSession](../../debugger/debug-interface-access/idiasession.md) zu öffnen, um Debuginformationen zu erhalten.  
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  Verwenden Sie die Methoden in `IDiaSession` verwendet, um die Symbole in der Datenquelle abzufragen.  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  Verwenden Sie die `IDiaEnum*`\-Schnittstellen, um die Symbole oder andere Elemente von Debuginformationen aufzulisten und zu überprüfen.  
  
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
  
## Siehe auch  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
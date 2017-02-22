---
title: "IDiaSession | Microsoft Docs"
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
  - "IDiaSession-Schnittstelle"
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Stellt einen Abfragekontext für Debugsymbole bereit.  
  
## Syntax  
  
```  
IDiaSession : IUnknown  
```  
  
## Methoden  
 Die folgende Tabelle zeigt die `IDiaSession`\-Methoden.  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDiaSession::get\_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Ruft die Ladeadresse der ausführbaren Datei ab, die den Symbolen in diesem Symbolspeicher entspricht.  Dies ist der gleiche Wert, der an die `put_loadAddress`\-Methode übergeben wurde.|  
|[IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Legt die Ladeadresse der ausführbaren Datei fest, die den Symbolen in diesem Symbolspeicher entspricht. **Note:**  Es ist wichtig, diese Methode aufrufen, wenn Sie ein `IDiaSession`\-Objekt abrufen, und bevor Sie anfangen, das Objekt zu verwenden.|  
|[IDiaSession::get\_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Ruft einen Verweis auf den globalen Bereich ab.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Ruft einen Enumerator für alle Tabellen ab, die im Symbolspeicher enthalten sind.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Ruft einen Enumerator für alle benannten Symbole an statischen Speicherorten ab.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Ruft alle untergeordneten Elemente eines angegebenen übergeordneten Bezeichners ab, die dem Namen und Symboltyp entsprechen.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Ruft einen bestimmten Symboltyp ab, der eine angegebene Adresse enthält oder dieser am nächsten kommt.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Ruft einen bestimmten Symboltyp ab, der eine angegebene relative virtuelle Adresse enthält oder dieser am nächsten kommt.|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Ruft einen bestimmten Symboltyp ab, der eine angegebene virtuelle Adresse enthält oder dieser am nächsten kommt.|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Ruft das Symbol ab, das das angegebene Metadatentoken enthält.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Überprüft, ob zwei Symbole übereinstimmen.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Ruft ein Symbol anhand des eindeutigen Bezeichners ab.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Ruft einen bestimmten Symboltyp ab, der eine angegebene relative virtuelle Adresse und einen Offset enthält oder diesen am nächsten kommt.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Ruft einen bestimmten Symboltyp ab, der eine angegebene virtuelle Adresse und einen Offset enthält oder diesen am nächsten kommt.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Ruft eine Quelldatei nach Kompiliereinheit und Namen ab.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Ruft eine Quelldatei nach Bezeichner der Quelldatei ab.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Ruft die Zeilennummern innerhalb eines angegebenen Kompiliereinheits\- und Quelldateibezeichners ab.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Ruft die Zeilen in einer bestimmten Kompiliereinheit ab, die eine angegebene Adresse enthalten.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Ruft die Zeilen in einer bestimmten Kompiliereinheit ab, die eine angegebene relative virtuelle Adresse enthalten.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Durchsucht die Zeilennummerninformationen nach Zeilen, die in einem bestimmten Adressbereich enthalten sind.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Ruft die Zeilen in einer bestimmten Kompiliereinheit nach Quelldatei und Zeilennummer ab.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Ruft eine Quelle ab, die im Symbolspeicher abgelegt wurde, und zwar nach Attributanbieter oder anderen Komponenten des Kompilierungsprozesses.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Ruft eine aufgelistete Sequenz von Debugdatenstreams ab.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, um alle inline Frames auf einer angegebenen Adresse zu durchlaufen.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, um alle inline Frames auf einer angegebenen relativen virtuellen Adresse RVA \(\) zu durchlaufen.|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, um alle inline Frames auf einer angegebenen virtuellen Adresse \(VA\) zu durchlaufen.|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, durch die Zeilennummerninformationen aller Funktionen direkt oder indirekt zu durchlaufen, die inline sind, durch das angegebene Symbol Elemente.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, durch die Zeilennummerninformationen aller Funktionen direkt oder indirekt zu durchlaufen, die inline sind, durch das angegebene Symbol und Elemente innerhalb des angegebenen Adressbereichs enthalten ist.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, durch die Zeilennummerninformationen aller Funktionen direkt oder indirekt zu durchlaufen, die inline sind, durch das angegebene Symbol und Elemente innerhalb der angegebenen relativen virtuellen Adresse RVA \(\) enthalten ist.|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, durch die Zeilennummerninformationen aller Funktionen direkt oder indirekt zu durchlaufen, die inline sind, durch das angegebene Symbol und Elemente innerhalb der angegebenen virtuellen Adresse \(VA\) enthalten ist.|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, durch die Zeilennummerninformationen aller Funktionen direkt oder indirekt zu durchlaufen, die inline sind, in der Quelldatei angegebenen und der Zeilennummer.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Ruft eine Enumeration ab, die einem Client ermöglicht, durch die Zeilennummerninformationen aller Inlinefunktionen zu durchlaufen, die einen angegebenen Namen übereinstimmen.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Gibt eine Enumeration von Symbolen für die Variablen zurückgegeben, dass der angegebene Tagwert in der übergeordneten Zugriffstastenstubfunktion entspricht.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Erstellen eines entsprechenden Tagwert angegeben, gibt diese Methode eine Enumeration von Symbolen zurück, die in einer angegebenen Elementen Zugriffstastenstubfunktion an einer angegebenen relativen virtuellen Adresse enthalten sind.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Gibt eine Enumeration von Symbolen für inline Frames gemäß dem angegebenen Inlinefunktionsnamen zurück.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Gibt eine Enumeration von Symbolen für inline Frames zurück, die dem angegebenen Quellspeicherort entsprechen.|  
  
## Hinweise  
 Es ist wichtig, die [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)\-Methode aufrufen, nachdem das `IDiaSession`\-Objekt erstellt wurde — und der Wert, der der `put_loadAddress`\-Methode übergeben wird, muss ungleich NULL sein — damit alle Eigenschaften der virtuellen Adresse \(VA\) von Symbolen zugreifbar sind.  Die Ladeadresse stammt von dem Programm, das die zum Debugging vorgesehene, ausführbare Datei geladen hat.  Beispielsweise können Sie die Win32\-Funktion `GetModuleInformation` aufrufen, um die Ladeadresse für die ausführbare Datei abzurufen, wenn ein Handle zur ausführbaren Datei gegeben ist.  
  
## Beispiel  
 Dieses Beispiel veranschaulicht, wie die `IDiaSession`\-Schnittstelle als Teil einer allgemeinen Initialisierung des DIAS SDK abgerufen wird.  
  
```cpp#  
CComPtr<IDiaDataSource> pSource;  
ComPtr<IDiaSession> psession;  
  
void InitializeDIA(const char *szFilename)  
{  
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,  
                                   NULL,  
                                   CLSCTX_INPROC_SERVER,  
                                   __uuidof( IDiaDataSource ),  
                                  (void **) &pSource);  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename,  
              szFilename,  
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    if ( FAILED( pSource->openSession( &psession ) ) )  
    {  
        Fatal( "openSession" );  
    }  
}  
```  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Übersicht](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Abfragen der PDB\-Datei](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
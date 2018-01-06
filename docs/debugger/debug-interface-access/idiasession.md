---
title: IDiaSession | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f3939ab86cd9f0948a2be44756b9ed94d143ecc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idiasession"></a>IDiaSession
Stellt einen Abfragekontext für die Debugsymbole bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Methoden  
 Die folgende Tabelle zeigt die Methoden der `IDiaSession`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Ruft die Adresse des für die ausführbare Datei, die die Symbole in diesem Symbolspeicher entspricht. Dies ist der gleiche Wert, der übergeben wurde die `put_loadAddress` Methode.|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Legt die Adresse des für die entsprechende ausführbare Datei auf die Symbole in dieser Symbolspeicher fest. **Hinweis:** es ist wichtig, diese Methode aufrufen, wenn Sie erhalten eine `IDiaSession` Objekt, und bevor Sie beginnen mit dem-Objekt.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Ruft einen Verweis auf den globalen Bereich ab.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Ruft einen Enumerator für alle Tabellen im Symbolspeicher ab.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Ruft einen Enumerator für alle benannten Symbole an statische Speicherorten ab.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Ruft alle untergeordneten Elemente einer angegebenen übergeordneten Element-ID, die den Namen und ein Symbol Typ entsprechen.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Ruft einen angegebenen Symboltyp, der an eine bestimmte Adresse am ehesten entspricht, oder enthält.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Ruft einen angegebenen Symboltyp, der am ehesten zu einem angegebenen relativen virtuellen Adresse (RVA) oder enthält.|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Ruft einen angegebenen Symboltyp, der am ehesten auf eine angegebene virtuelle Adresse ("VA" ist) oder enthält.|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Ruft das Symbol, das angegebene Metadatentoken ab.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Überprüft, um festzustellen, ob zwei Symbole äquivalent sind.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Ruft ein Symbol, das durch seinen eindeutigen Bezeichner ab.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Ruft einen angegebenen Symboltyp, der am ehesten zu einem angegebenen relativen virtuellen Adresse und einem festen Offset oder enthält.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Ruft einen angegebenen Symboltyp, der am ehesten zu einem angegebenen virtuellen Adresse und einem festen Offset oder enthält.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Ruft eine Quelldatei von Kompiliereinheit und Namen ab.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Ruft eine Quelldatei von Datei-ID ab.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Ruft die zeilennummerierung innerhalb einer angegebenen Dateibezeichner Kompiliereinheit und Quelle ab.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Ruft ab, die Zeilen in einer angegebenen Kompiliereinheit, die eine bestimmten Adresse enthalten.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Ruft ab, die Zeilen in einer angegebenen Kompiliereinheit, die eine angegebene relative virtuelle Adresse enthalten.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Sucht die Zeilennummerninformationen für Zeilen, die in einen angegebenen Adressbereich enthalten.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Ruft ab, die Zeilen in einer angegebenen Kompiliereinheit von Source-Datei und die Zeilennummer an.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Ruft ab eine Quelle, die in den Symbolspeicher von Attribut Anbietern oder andere Komponenten den Kompilierungsprozess platziert wurde.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Ruft eine enumerierte Sequenz von Debug-Datenströme.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Ruft eine Enumeration, die von einem Client zum iterieren durch alle Inlineframes auf einer angegebenen Adresse ermöglichen.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Ruft eine Enumeration, die von einem Client zum iterieren durch alle Inlineframes auf einer angegebenen relativen virtuellen Adresse (RVA) ermöglichen.|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Ruft eine Enumeration, die einen Client zum iterieren durch alle Inlineframes auf einer bestimmten virtuellen Adresse ("VA" ist) ermöglicht.|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Ruft eine Enumeration, die ermöglicht einem Client zu durchlaufen und die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt mit dem angegebenen übergeordneten Symbol ab.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Ruft eine Enumeration, die ermöglicht einem Client zu durchlaufen und die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt mit dem angegebenen übergeordneten-Symbol, und innerhalb der angegebenen Adressbereich enthalten sind.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Ruft eine Enumeration, die ermöglicht einem Client zu durchlaufen und die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt mit dem angegebenen übergeordneten Symbol und befinden sich innerhalb der angegebenen relativen virtuellen Adresse (RVA) ab.|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Ruft eine Enumeration, die ermöglicht einem Client zu durchlaufen und die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt mit dem angegebenen übergeordneten Symbol und befinden sich innerhalb der angegebenen virtuellen Adresse ("VA" ist).|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Ruft eine Enumeration, die ermöglicht einem Client zum iterieren durch die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt in die angegebene Quelle und die Zeilennummer der Anzahl ab.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Ruft eine Enumeration, die ermöglicht einem Client zum iterieren durch die Zeilennummerninformationen aller Inline-Funktionen, die mit den angegebenen Namen übereinstimmen.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Gibt eine Enumeration von Symbolen für die Variable, die Wert für das angegebene Tag entspricht in der übergeordneten Tabelle Accelerator-Stub-Funktion zurück.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Wenn einen entsprechenden Tagwert, gibt diese Methode eine Enumeration von Symbolen, die enthalten sind in einer angegebenen übergeordneten Accelerator Stub-Funktion in einem angegebenen relativen virtuellen Adresse an.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Gibt eine Enumeration von Symbolen für Inlineframes, den Namen der angegebenen Inline-Funktion entspricht.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Gibt eine Enumeration von Symbolen für Inlineframes entsprechen, die mit dem angegebenen Quellspeicherort zurück.|  
  
## <a name="remarks"></a>Hinweise  
 Es ist wichtig, rufen Sie die [idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) Methode nach dem Erstellen der `IDiaSession` Objekt – und der an übergebene Wert den `put_loadAddress` Methode muss ungleich NULL sein – für alle Eigenschaften der virtuellen Adresse ("VA" ist) der Symbole werden zugegriffen werden kann. Adresse des stammen aus der Anwendung der debuggten, ausführbaren Datei geladen. Sie können z. B. die Win32-Funktion aufrufen `GetModuleInformation` abzurufenden Adresse des für die ausführbare Datei, ein Handle an die ausführbare Datei übergeben.  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird gezeigt, wie zum Abrufen der `IDiaSession` -Schnittstelle als Teil einer allgemeinen Initialisierung DIA-SDK.  
  
```C++  
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
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: "MSDIA80.dll"  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Übersicht](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [EXE-Datei](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [Idiasymbol:: Findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Abfragen der PDB-Datei](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
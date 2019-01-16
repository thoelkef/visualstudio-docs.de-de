---
title: IDiaSession | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d469ea89b7ef5f09296fce03fa10c47a7500e52e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923834"
---
# <a name="idiasession"></a>IDiaSession
Stellt einen Abfragekontext für Debugsymbole bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Methoden  
 Die folgende Tabelle zeigt die Methoden der `IDiaSession`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Ruft ab die Ladeadresse für die ausführbare Datei, die die Symbole in diesem Symbolspeicher entspricht. Dies ist der gleiche Wert, der übergeben wurde die `put_loadAddress` Methode.|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Legt die Ladeadresse für die ausführbare Datei, die entspricht auf die Symbole in diesem Symbolspeicher fest. **Hinweis**:  Es ist wichtig, diese Methode aufrufen, wenn Sie erhalten eine `IDiaSession` Objekt aus, und bevor Sie beginnen mit dem Objekt.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Ruft einen Verweis auf den globalen Bereich ab.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Ruft einen Enumerator für alle Tabellen im Symbolspeicher ab.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Ruft einen Enumerator für alle benannten Symbole an statische Speicherorten ab.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Ruft alle untergeordneten Elemente einer angegebenen übergeordneten Element-ID, die den Namen und Symbol Datentyp entsprechen.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Ruft einen bestimmtes Symbol-Typ, der enthält, oder an eine bestimmte Adresse am nächsten ist.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Ruft einen bestimmtes Symbol-Typ, der enthält, oder um eine angegebene relative virtuelle Adresse (RVA) am nächsten ist.|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Ruft einen bestimmtes Symbol-Typ, der enthält, oder um eine angegebene virtuelle Adresse (VA) am nächsten ist.|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Ruft ab, das Symbol, das ein Token für die angegebenen Metadaten enthält.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Überprüft, um festzustellen, ob zwei Symbole entsprechen.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Ruft ein Symbol durch seinen eindeutigen Bezeichner ab.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Ruft ein bestimmtes Symbol-Typ, der enthält und am nächsten ist, einen angegebenen relativen virtuellen Adresse und den Offset ab.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Ruft ein bestimmtes Symbol-Typ, der enthält und am nächsten ist, eine angegebene virtuelle Adresse und den Offset ab.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Ruft eine Quelldatei von Kompiliereinheit und den Namen ab.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Ruft eine Quelldatei von Datei-ID ab.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Ruft die zeilennummerierung innerhalb einer angegebenen Kompiliereinheit und Quelle-Datei-ID ab.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Ruft ab, die Zeilen in einer angegebenen Kompiliereinheit, die eine bestimmten Adresse enthalten.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Ruft ab, die Zeilen in einer angegebenen Kompiliereinheit, die eine angegebene relative virtuelle Adresse enthalten.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Sucht nach den Informationen zur Zeilennummer für Zeilen in einen angegebenen Adressbereich.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Ruft die Zeilen in einer angegebenen Kompiliereinheit nach Anzahl für Quelle und die Zeilennummer ab.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Ruft ab eine Quelle, die in den Symbolspeicher vom Attributanbieter oder andere Komponenten des Kompilierungsprozesses abgelegt wurden.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Ruft eine aufgelistete Sequenz von Debug-Datenströme.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Ruft eine Enumeration, die einem Client zum iterieren durch alle Inlineframes auf einer bestimmten Adresse ermöglicht.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Ruft eine Enumeration, die einem Client zum iterieren durch alle Inlineframes auf eine angegebene relative virtuelle Adresse (RVA) ermöglicht.|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Ruft eine Enumeration, die einem Client zum iterieren durch alle Inlineframes auf eine angegebene virtuelle Adresse (VA) ermöglicht.|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Ruft eine Enumeration, die ermöglicht es einem Client zu durchlaufen und die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt durch das Symbol des angegebenen übergeordneten Elements ab.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Ruft eine Enumeration, die ermöglicht es einem Client zu durchlaufen und die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt durch das angegebene übergeordnete-Symbol und befinden sich innerhalb des Bereichs der angegebenen Adresse an.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Ruft eine Enumeration, die ermöglicht es einem Client zu durchlaufen und die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt durch das angegebene übergeordnete-Symbol und befinden sich in die angegebene relative virtuelle Adresse (RVA) ab.|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Ruft eine Enumeration, die ermöglicht es einem Client zu durchlaufen und die Zeilennummerninformationen aller Funktionen, die inline erweitert wird, direkt oder indirekt durch das angegebene übergeordnete-Symbol und befinden sich innerhalb der angegebenen virtuellen Adresse (VA) ab.|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Ruft eine Enumeration, die ermöglicht einem Client die Zeilennummerninformationen aller Funktionen durchlaufen, die inline erweitert wird, direkt oder indirekt in die angegebene Quelle Quelldatei- und Zeileninformationen Anzahl ab.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Ruft eine Enumeration, die erlaubt einem Client, durchlaufen die Zeilennummerninformationen aller Inline-Funktionen, die mit den angegebenen Namen übereinstimmen.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Gibt eine Enumeration von Symbolen für die Variable, die der angegebenen Tagwert entspricht, in der übergeordneten Accelerator-Stub-Funktion zurück.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Wenn einen entsprechenden Tagwert, gibt diese Methode in einer angegebenen übergeordneten Accelerator-Stub-Funktion an eine angegebene relative virtuelle Adresse eine Enumeration von Symbolen, die enthalten sind.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Gibt eine Enumeration von Symbolen für Inlineframes, die für den Namen der Funktion Inline angegeben.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Gibt eine Enumeration von Symbolen für Inlineframes, die entsprechen zum Speicherort angegebenen Quelle zurück.|  
  
## <a name="remarks"></a>Hinweise  
 Es ist wichtig, rufen Sie die [idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) Methode nach dem Erstellen der `IDiaSession` Objekt – und den übergebenen Wert die `put_loadAddress` Methode muss einen Wert ungleich – für alle virtuelle Adresse (VA) Eigenschaften von Symbolen sein zugegriffen werden kann. Die Ladeadresse stammt jedes beliebige Programm der debuggten, ausführbaren Datei geladen. Sie können z. B. die Win32-Funktion aufrufen `GetModuleInformation` abzurufenden Ladeadresse für die ausführbare Datei, ein Handle an die ausführbare Datei übergeben.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie Sie erhalten die `IDiaSession` -Schnittstelle als Teil einer allgemeinen Initialisierung die DIA-SDK.  
  
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
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Abfragen der PDB-Datei](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
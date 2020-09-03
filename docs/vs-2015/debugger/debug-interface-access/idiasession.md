---
title: IDiaSession | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 002e7198210e123fc2461f712bb8db442b9f25c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190720"
---
# <a name="idiasession"></a>IDiaSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Stellt einen Abfrage Kontext für Debugsymbole bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Methoden  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDiaSession` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Ruft die Lade Adresse für die ausführbare Datei ab, die den Symbolen in diesem Symbol Speicher entspricht. Dabei handelt es sich um denselben Wert, der an die-Methode übermittelt wurde `put_loadAddress` .|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Legt die Lade Adresse für die ausführbare Datei fest, die den Symbolen in diesem Symbol Speicher entspricht. **Hinweis:**  Es ist wichtig, diese Methode aufzurufen, wenn Sie ein `IDiaSession` -Objekt erhalten und bevor Sie mit der Verwendung des-Objekts beginnen.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Ruft einen Verweis auf den globalen Gültigkeitsbereich ab.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Ruft einen Enumerator für alle Tabellen ab, die im Symbol Speicher enthalten sind.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Ruft einen Enumerator für alle benannten Symbole an statischen Speicherorten ab.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Ruft alle untergeordneten Elemente eines angegebenen übergeordneten Bezeichners ab, die dem Namen und dem Symboltyp entsprechen.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Ruft einen angegebenen Symboltyp ab, der eine angegebene Adresse enthält bzw. am nächsten liegt.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Ruft einen angegebenen Symboltyp ab, der eine angegebene relative virtuelle Adresse (RVA) enthält oder der am nächsten liegt.|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Ruft einen angegebenen Symboltyp ab, der eine angegebene virtuelle Adresse (VA) enthält bzw. am nächsten liegt.|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Ruft das Symbol ab, das ein angegebenes Metadatentoken enthält.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Prüft, ob zwei Symbole äquivalent sind.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Ruft ein Symbol anhand seines eindeutigen Bezeichners ab.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Ruft einen angegebenen Symboltyp ab, der eine angegebene relative virtuelle Adresse und einen angegebenen Offset enthält bzw. am nächsten liegt.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Ruft einen angegebenen Symboltyp ab, der eine angegebene virtuelle Adresse und einen angegebenen Offset enthält bzw. am nächsten liegt.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Ruft eine Quelldatei nach dem Kompilieren und dem Namen ab.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Ruft eine Quelldatei nach dem Quelldatei Bezeichner ab.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Ruft Zeilennummern innerhalb eines angegebenen Kompilierungen und Quelldatei Bezeichners ab.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Ruft die Zeilen in einer angegebenen Kompilierungen ab, die eine angegebene Adresse enthalten.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Ruft die Zeilen in einer angegebenen Kompilierungen ab, die eine angegebene relative virtuelle Adresse enthalten.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Sucht die Zeilennummern Informationen für Zeilen, die in einem angegebenen Adressbereich enthalten sind.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Ruft die Zeilen in einer angegebenen Kompilierungen nach Quelldatei und Zeilennummer ab.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Ruft eine Quelle ab, die von Attribut Anbietern oder anderen Komponenten des Kompilierungsprozesses im Symbol Speicher abgelegt wurde.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Ruft eine aufgelistete Sequenz von Debug-Datenströmen ab.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Ruft eine Enumeration ab, mit der ein Client alle Inline Rahmen einer bestimmten Adresse durchlaufen kann.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Ruft eine Enumeration ab, mit der ein Client alle Inline Rahmen einer angegebenen relativen virtuellen Adresse (RVA) durchlaufen kann.|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Ruft eine Enumeration ab, mit der ein Client alle Inline Rahmen einer angegebenen virtuellen Adresse (VA) durchlaufen kann.|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Ruft eine Enumeration ab, die es einem Client ermöglicht, die Zeilennummern Informationen aller Funktionen zu durchlaufen, die direkt oder indirekt durch das angegebene übergeordnete Symbol Inline sind.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Ruft eine Enumeration ab, die es einem Client ermöglicht, die Zeilennummerinformationen aller Funktionen, die direkt oder indirekt durch das angegebene übergeordnete Symbol eingebunden sind, zu durchlaufen und innerhalb des angegebenen Adress Bereichs enthalten sind.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Ruft eine Enumeration ab, mit der ein Client die Zeilennummerinformationen aller Funktionen durchlaufen kann, die direkt oder indirekt durch das angegebene übergeordnete Symbol Inline sind und in der angegebenen relativen virtuellen Adresse (RVA) enthalten sind.|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Ruft eine Enumeration ab, mit der ein Client die Zeilennummerinformationen aller Funktionen, die direkt oder indirekt durch das angegebene übergeordnete Symbol eingebunden sind und in der angegebenen virtuellen Adresse (VA) enthalten sind, durchlaufen kann.|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Ruft eine Enumeration ab, mit der ein Client die Zeilennummern Informationen aller Funktionen, die direkt oder indirekt in der angegebenen Quelldatei und Zeilennummer Inline sind, durchlaufen kann.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Ruft eine Enumeration ab, die es einem Client ermöglicht, die Zeilennummern Informationen aller Inline Funktionen zu durchlaufen, die mit einem angegebenen Namen übereinstimmen.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Gibt eine Enumeration von Symbolen für die Variable zurück, der der angegebene Tagwert in der übergeordneten Accelerator-stubfunktion entspricht.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Wenn ein entsprechender Tagwert angegeben ist, gibt diese Methode eine Enumeration von Symbolen zurück, die in einer angegebenen relativen virtuellen Adresse enthalten sind.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Gibt eine Enumeration von Symbolen für Inline Frames zurück, die dem angegebenen Inline Funktionsnamen entsprechen.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Gibt eine Enumeration von Symbolen für Inline Frames zurück, die dem angegebenen Quell Speicherort entsprechen.|  
  
## <a name="remarks"></a>Bemerkungen  
 Es ist wichtig, dass Sie nach dem Erstellen des Objekts – die Methode [IDiaSession::p ut_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) `IDiaSession` und der an die Methode weiter gegebene Wert `put_loadAddress` – für alle Eigenschaften der virtuellen Adresse (VA), auf die zugegriffen werden kann, nicht NULL sein. Die Lade Adresse stammt von dem Programm, das die zu debuggenden ausführbare Datei geladen hat. Beispielsweise können Sie die Win32-Funktion aufrufen, `GetModuleInformation` um die Lade Adresse für die ausführbare Datei abzurufen, wenn ein Handle für die ausführbare Datei angegeben wird.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt, wie die- `IDiaSession` Schnittstelle im Rahmen einer allgemeinen Initialisierung der DIA SDK abgerufen wird.  
  
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
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Übersicht über](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Speichert](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [Idiasymmetribol:: findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Abfragen der PDB-Datei](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)

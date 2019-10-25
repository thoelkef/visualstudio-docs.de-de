---
title: IDiaDataSource | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 453be1d77f1d2b1759e3de4433225cf97d026054
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744908"
---
# <a name="idiadatasource"></a>IDiaDataSource
Initiiert den Zugriff auf eine Quelle von Debugsymbolen.

## <a name="syntax"></a>Syntax

```
IDiaDataSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
In der folgenden Tabelle sind die Methoden von `IDiaDataSource` aufgeführt.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Ruft den Dateinamen für den letzten Ladefehler ab.|
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Öffnet eine Programm Datenbankdatei (PDB-Datei) als debugdatenquelle und bereitet Sie vor.|
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Öffnet und überprüft, ob die Programm Datenbankdatei (PDB-Datei) mit den bereitgestellten Signatur Informationen übereinstimmt. bereitet die PDB-Datei als debugdatenquelle vor.|
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Öffnet und bereitet die der exe-/dll-Datei zugeordneten Debugdaten vor.|
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Bereitet die Debugdaten vor, die in einer Programm Datenbankdatei (PDB-Datei) gespeichert sind, auf die über einen Speicher internen Datenstrom zugegriffen wird|
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Öffnet eine Sitzung zum Abfragen von Symbolen.|

## <a name="remarks"></a>Hinweise
Wenn Sie eine der Load-Methoden der `IDiaDataSource`-Schnittstelle aufzurufen, wird die Symbol Quelle geöffnet. Ein erfolgreicher Abruf der [IDiaDataSource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) -Methode gibt eine [IDiaSession](../../debugger/debug-interface-access/idiasession.md) -Schnittstelle zurück, die die Abfrage der Datenquelle unterstützt. Wenn die Load-Methode einen Datei bezogenen Fehler zurückgibt, enthält der [IDiaDataSource:: get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) -Methodenrückgabewert den Dateinamen, der dem Fehler zugeordnet ist.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Diese Schnittstelle wird durch Aufrufen der `CoCreateInstance`-Funktion mit dem Klassen Bezeichner `CLSID_DiaSource` und der Schnittstellen-ID `IID_IDiaDataSource` abgerufen. Das Beispiel zeigt, wie diese Schnittstelle abgerufen wird.

## <a name="example"></a>Beispiel

```C++

      IDiaDataSource* pSource;
HRESULT hr = CoCreateInstance(CLSID_DiaSource,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaDataSource,
                              (void**) &pSource);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Anforderungen
Header: Dia2.h

Bibliothek: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)

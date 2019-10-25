---
title: 'IDiaDataSource:: loadDataFromPdb | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7526ba6e62c9df22a2338adc80f5d56578502cdb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744940"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Öffnet eine Programm Datenbankdatei (PDB-Datei) als debugdatenquelle und bereitet Sie vor.

## <a name="syntax"></a>Syntax

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>Parameter
pdbPath

in Der Pfad zur PDB-Datei.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. In der folgenden Tabelle sind die möglichen Rückgabewerte für diese Methode aufgeführt.

|Wert|Beschreibung|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Die Datei konnte nicht geöffnet werden, oder es wurde festgestellt, dass die Datei ein ungültiges Format aufweist.|
|E_PDB_FORMAT|Es wurde versucht, auf eine Datei mit einem veralteten Format zuzugreifen.|
|E_INVALIDARG|Ungültiger Parameter.|
|E_UNEXPECTED|Die Datenquelle wurde bereits vorbereitet.|

## <a name="remarks"></a>Hinweise
Diese Methode lädt die Debugdaten direkt aus einer PDB-Datei.

Verwenden Sie die [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) -Methode, um die PDB-Datei mit bestimmten Kriterien zu validieren.

Verwenden Sie die Methode [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) , um Zugriff auf den Daten Ladevorgang zu erhalten (über einen Rückrufmechanismus).

Verwenden Sie die [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) -Methode, um eine PDB-Datei direkt aus dem Arbeitsspeicher zu laden.

## <a name="example"></a>Beispiel

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>Siehe auch
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)

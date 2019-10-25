---
title: 'IDiaDataSource:: loadDataFromIStream | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b2bcf657b4404ed72059351175d124a9c07abb46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744951"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
Bereitet die Debugdaten vor, die in einer Programm Datenbankdatei (PDB-Datei) gespeichert sind, auf die über einen Speicher internen Datenstrom zugegriffen wird

## <a name="syntax"></a>Syntax

```C++
HRESULT loadDataFromIStream ( 
   IStream* pIStream
);
```

#### <a name="parameters"></a>Parameter
 pIStream

in Ein <xref:IStream>-Objekt, das den zu verwendenden Datenstrom darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. In der folgenden Tabelle sind die möglichen Rückgabewerte für diese Methode aufgeführt.

|Wert|Beschreibung|
|-----------|-----------------|
|E_PDB_FORMAT|Es wurde versucht, auf eine Datei mit einem veralteten Format zuzugreifen.|
|E_INVALIDARG|Ungültiger Parameter.|
|E_UNEXPECTED|Die Datenquelle wurde bereits vorbereitet.|

## <a name="remarks"></a>Hinweise
 Diese Methode ermöglicht es, dass die Debugdaten für eine ausführbare Datei über ein <xref:IStream> Objekt aus dem Arbeitsspeicher abgerufen werden.

 Wenn Sie eine PDB-Datei ohne Validierung laden möchten, verwenden Sie die [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) -Methode.

 Verwenden Sie die [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) -Methode, um die PDB-Datei mit bestimmten Kriterien zu validieren.

 Verwenden Sie die Methode [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) , um Zugriff auf den Daten Ladevorgang zu erhalten (über einen Rückrufmechanismus).

## <a name="see-also"></a>Siehe auch
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
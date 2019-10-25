---
title: IDiaReadExeAtOffsetCallback | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback interface
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f8498b0189a1d5bfb876417d4719adb3487065d5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742813"
---
# <a name="idiareadexeatoffsetcallback"></a>IDiaReadExeAtOffsetCallback
Ermöglicht es einer Client Anwendung, Bytes einer ausführbaren Datei anzugeben, wie in der Dateiposition angegeben.

## <a name="syntax"></a>Syntax

```
IDiaReadExeAtOffsetCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von `IDiaReadExeAtOffsetCallback` aufgeführt.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|Liest die angegebene Anzahl von Bytes ab dem angegebenen Offset aus einer ausführbaren Datei.|

## <a name="remarks"></a>Hinweise
 Die Client Anwendung implementiert diese Schnittstelle, um die Bytes der ausführbaren Datei mithilfe eines absoluten Offsets in der Datei der ausführbaren Datei bereitzustellen. Um eine relative virtuelle Adresse zu verwenden, implementieren Sie die [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) -Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Methode wird von der Client Anwendung implementiert und an die Methode [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) als alternative Methode zum Lesen der Datei übergeben.

## <a name="requirements"></a>Anforderungen
 Header: Dia2.h

 Bibliothek: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
---
title: IDiaReadExeAtRVACallback | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2aee44ff3acc1d7423e19de8fd64be0e46d8e372
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742803"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Ermöglicht es einer Client Anwendung, Bytes einer ausführbaren Datei bereitzustellen, wie durch eine relative virtuelle Adresse angegeben.

## <a name="syntax"></a>Syntax

```
IDiaReadExeAtRVACallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von `IDiaReadExeAtRVACallback` aufgeführt.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Liest die angegebene Anzahl von Bytes ab der angegebenen relativen virtuellen Adresse (RVA) aus der ausführbaren Datei.|

## <a name="remarks"></a>Hinweise
 Die Client Anwendung implementiert diese Schnittstelle, um die Bytes der ausführbaren Datei mit einer relativen virtuellen Adresse in der Datei der ausführbaren Datei bereitzustellen. Um einen absoluten Dateioffset zu verwenden, implementieren Sie die [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) -Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Methode wird von der Client Anwendung implementiert und an die Methode [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) als alternative Methode zum Lesen der Datei übergeben.

## <a name="requirements"></a>Anforderungen
 Header: Dia2.h

 Bibliothek: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
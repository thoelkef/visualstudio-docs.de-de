---
title: IDiaLoadCallback | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ca58a206fec15bb8a9ae7f68a278a4530be47d8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743041"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
Empfängt Rückrufe aus dem Dia-Symbol zum Suchen der Prozedur und ermöglicht so eine Benutzeroberfläche, um den Status des Orts Versuchs zu melden.

## <a name="syntax"></a>Syntax

```
IDiaLoadCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgenden Methoden werden von dieser Schnittstelle verfügbar gemacht:

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|Wird aufgerufen, wenn ein Debugverzeichnis in der exe-Datei gefunden wurde.|
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|Wird aufgerufen, wenn eine Candidate. dbg-Datei geöffnet wurde.|
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|Wird aufgerufen, wenn eine Candidate. PDB-Datei geöffnet wurde.|
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|Bestimmt, ob Registrierungs Abfragen verwendet werden können, um Symbol Suchpfade zu suchen.|
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|Bestimmt, ob der Zugriff auf einen Symbol Server zum Auflösen von Symbolen zulässig ist.|

## <a name="remarks"></a>Hinweise
 Die Client Anwendung implementiert diese Schnittstelle und stellt im Aufrufe der [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) -Methode einen Verweis darauf bereit.

 Weitere Einschränkungen, die für einen Ladevorgang erzwungen werden können, finden Sie unter der [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) -Schnittstelle.

## <a name="requirements"></a>Anforderungen
 Header: Dia2.h

 Bibliothek: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
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
ms.openlocfilehash: c86a0e995e3336bc217bcc9ad0e7ce28a6434478
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597139"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Ermöglicht eine Clientanwendung Bytes einer ausführbaren Datei gemäß der eine relative virtuelle Adresse angeben.

## <a name="syntax"></a>Syntax

```
IDiaReadExeAtRVACallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDiaReadExeAtRVACallback`.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Liest die angegebene Anzahl von Bytes, beginnend ab der angegebenen relativen virtuellen Adresse (RVA) der ausführbaren Datei an.|

## <a name="remarks"></a>Anmerkungen
 Die Client-Anwendung implementiert diese Schnittstelle, um die Bytes der ausführbaren Datei mit der eine relative virtuelle Adresse in der ausführbaren Datei Datei bereitzustellen. Um eine absolute Dateioffset verwenden zu können, implementieren die [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Methode implementiert, die von der Clientanwendung und übergeben die [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode als eine alternative Methode zum Lesen der Datei.

## <a name="requirements"></a>Anforderungen
 Header: Dia2.h

 Bibliothek: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
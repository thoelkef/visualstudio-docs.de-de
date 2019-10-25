---
title: IDiaStackWalker | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2366c933bf072c295b29d06ff5610bd3735c0077
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741519"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Stellt Methoden bereit, mit denen ein Stapel Durchlauf mithilfe von Informationen in der PDB-Datei durchgeführt werden kann.

## <a name="syntax"></a>Syntax

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
In der folgenden Tabelle sind die Methoden von `IDiaStackWalker` aufgeführt.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Ruft einen Stapel Rahmen Enumerator für x86-Plattformen ab.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Ruft einen Stapel Rahmen Enumerator für einen bestimmten Plattformtyp ab.|

## <a name="remarks"></a>Hinweise
Diese Schnittstelle wird verwendet, um eine Liste der Stapel Rahmen für ein geladenes Modul zu erhalten. Jeder Methode wird ein [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) -Objekt, das von der Client Anwendung implementiert wird, übermittelt, das die erforderlichen Informationen zum Erstellen der Liste der Stapel Rahmen bereitstellt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
Diese Schnittstelle wird durch Aufrufen der `CoCreateInstance`-Methode mit dem Klassen Bezeichner `CLSID_DiaStackWalker` und der Schnittstellen-ID von `IID_IDiaStackWalker` abgerufen. Das Beispiel zeigt, wie diese Schnittstelle abgerufen wird.

## <a name="example"></a>Beispiel
Dieses Beispiel zeigt, wie Sie die `IDiaStackWalker`-Schnittstelle abrufen.

```C++

IDiaStackWalker* pStackWalker;
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaStackWalker,
                              (void**) &pStackWalker);
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
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)

---
title: 'Idialoadcallback:: Notifydebugdir | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce251da3c1cb7b1da00971d46cc0801ad24b8985
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839822"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Aufgerufen, wenn ein Debugverzeichnis in die .exe-Datei gefunden wurde.

## <a name="syntax"></a>Syntax

```C++
HRESULT NotifyDebugDir ( 
   BOOL  fExecutable,
   DWORD cbData,
   BYTE  data[]
);
```

#### <a name="parameters"></a>Parameter
 `fExecutable`

[in] `TRUE` Wenn das Debugverzeichnis aus einer ausführbaren Datei (statt eine DBG-Datei) gelesen wird.

 `cbData`

[in] Die Anzahl der Bytes der Daten in der Debugverzeichnis.

 `data[]`

[in] Ein Array, das mit das Debugverzeichnis gefüllt ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Der Rückgabecode wird in der Regel ignoriert.

## <a name="remarks"></a>Hinweise
 Die [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode dieser Rückruf aufruft, wenn beim Verarbeiten der ausführbaren Datei ein Debugverzeichnis gefunden.

 Diese Methode entfernt die Notwendigkeit für den Client für das reverse Engineering der ausführbaren Datei bzw. das Debug-Datei zur Unterstützung von Debuginformationen nicht in der PDB-Datei gefunden. Mit diesen Daten kann der Client erkennen, den Typ der Debuginformationen zur Verfügung und gibt an, ob es sich in die ausführbare Datei oder die DBG-Datei befindet.

 Die meisten Clients werden dieser Rückruf nicht erforderlich, da die `IDiaDataSource::loadDataForExe` -Methode öffnet transparent sowohl PDB .dbg-Dateien und bei Bedarf, um Symbole zu verarbeiten.

## <a name="see-also"></a>Siehe auch
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
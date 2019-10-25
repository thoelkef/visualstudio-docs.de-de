---
title: 'IDiaLoadCallback:: notifydebug-Verzeichnis | Microsoft-Dokumentation'
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
ms.openlocfilehash: 6618440cab9b9042ec371383f6c809ca1d0d11f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743088"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Wird aufgerufen, wenn ein Debugverzeichnis in der exe-Datei gefunden wurde.

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

[in] `TRUE`, wenn das Debugverzeichnis aus einer ausführbaren Datei gelesen wird (anstatt einer dbg-Datei).

 `cbData`

in Anzahl der Daten Bytes im Debugverzeichnis.

 `data[]`

in Ein Array, das mit dem Debugverzeichnis ausgefüllt ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. Der Rückgabecode wird in der Regel ignoriert.

## <a name="remarks"></a>Hinweise
 Die [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) -Methode ruft diesen Rückruf auf, wenn beim Verarbeiten der ausführbaren Datei ein Debugverzeichnis gefunden wird.

 Durch diese Methode entfällt die Notwendigkeit, dass der Client die ausführbare Datei und/oder Debugdatei rückgängig machen muss, um andere Debuginformationen als in der PDB-Datei zu unterstützen. Mit diesen Daten kann der Client den Typ der verfügbaren Debuginformationen erkennen und davon, ob er sich in der ausführbaren Datei oder der dbg-Datei befindet.

 Die meisten Clients benötigen diesen Rückruf nicht, da durch die `IDiaDataSource::loadDataForExe`-Methode bei Bedarf transparent sowohl PDB-als auch dbg-Dateien geöffnet werden.

## <a name="see-also"></a>Siehe auch
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
---
title: 'IDiaFrameData:: Execute | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88c9af8293dfc6a35e5f0e42d9596494d74b10aa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743686"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Führt die Stapel Auflösung aus und gibt die Ergebnisse in einer Stapel Durchlauf-Frame Schnittstelle zurück.

## <a name="syntax"></a>Syntax

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>Parameter
 `frame`

in Ein [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) -Objekt, das den Zustand von Frame Registern enthält.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben. In der folgenden Tabelle sind die möglichen Rückgabewerte für diese Methode aufgeführt.

|Wert|Beschreibung|
|-----------|-----------------|
|E_DIA_INPROLOG|Ein Stapel Rahmen kann im Prologcode nicht ausgeführt werden.|
|E_DIA_SYNTAX|Analysefehler im Rahmenprogramm.|
|E_DIA_FRAME_ACCESS|Auf die Register oder den Arbeitsspeicher kann nicht zugegriffen werden.|
|E_DIA_VALUE|Fehler bei der Berechnung eines Werts (z. b. Division durch null).|

## <a name="remarks"></a>Hinweise
 Diese Methode wird während des Debuggens aufgerufen, um den Stapel zu entladen. Das [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) -Objekt wird von der Client Anwendung implementiert, um Aktualisierungen der Register zu empfangen und von der `execute` Methode verwendete Methoden bereitzustellen.

## <a name="see-also"></a>Siehe auch
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
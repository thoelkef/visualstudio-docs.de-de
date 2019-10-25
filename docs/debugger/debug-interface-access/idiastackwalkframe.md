---
title: IDiaStackWalkFrame | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b2657127726e387e81a5b28c639abbaa5399019
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741438"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
Verwaltet den Stapel Kontext zwischen Aufrufen der [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) -Methode.

## <a name="syntax"></a>Syntax

```
IDiaStackWalkFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von `IDiaStackWalkFrame` aufgeführt.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Ruft den Wert eines Register ab.|
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Legt den Wert eines Register fest.|
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Liest Speicher aus dem Image.|
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Durchsucht den angegebenen Stapel Rahmen nach der nächstgelegenen Rückgabeadresse der Funktion.|
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Durchsucht den angegebenen Stapel Rahmen nach einer Rückgabeadresse an oder in der Nähe der angegebenen Adresse.|

## <a name="remarks"></a>Hinweise
 Diese Schnittstelle wird während der Ausführung des Programms zum Lesen und Schreiben von Registern sowie zum Zugreifen auf den Speicher und zum Suchen von Rückgabe Adressen verwendet.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die Client Anwendung implementiert diese Schnittstelle und übergibt eine Instanz der Schnittstelle an die [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) -Methode. Dieselbe Instanz dieser Schnittstelle wird erneut und erneut verwendet, um den Status der Register bei jedem Aufruf der `execute` Methode beizubehalten. Die `execute`-Methode verwendet diese Schnittstelle auch, um die Rückgabeadresse zu bestimmen.

## <a name="requirements"></a>Anforderungen
 Header: Dia2.h

 Bibliothek: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)
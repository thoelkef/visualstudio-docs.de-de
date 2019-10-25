---
title: IDiaStackWalkHelper | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40c2b58778b2a1073b31acc7007388d8e8fe222c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741306"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Ermöglicht das Durchlaufen des Stapels mithilfe der Programm-Debug-Datenbankdatei (PDB-Datei).

## <a name="syntax"></a>Syntax

```

IDiaStackWalkHelper: IUnknown

```

## <a name="methods-in-vtable-order"></a>Methoden in VTable-Reihenfolge
 In der folgenden Tabelle sind die Methoden `IDiaStackWalkHelper` aufgeführt:

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Ruft den Wert eines Register ab.|
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Legt den Wert eines Register fest.|
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Liest einen Datenblock aus dem Image der ausführbaren Datei im Arbeitsspeicher.|
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Durchsucht den angegebenen Stapel Rahmen nach der nächstgelegenen Rückgabeadresse der Funktion.|
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Durchsucht den angegebenen Stapel Rahmen nach einer Rückgabeadresse an oder in der Nähe der angegebenen Stapel Adresse.|
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Ruft den Stapel Rahmen ab, der die angegebene virtuelle Adresse enthält.|
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Ruft das Symbol ab, das die angegebene virtuelle Adresse enthält. **Hinweis:**  Das Symbol muss den Typ "`SymTagFunctionType`" aufweisen (ein Wert aus der Enumeration " [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) ").|
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Gibt den pData-Datenblock zurück, der der angegebenen virtuellen Adresse zugeordnet ist.|
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Ruft die virtuelle Startadresse einer ausführbaren Datei ab, wenn eine virtuelle Adresse irgendwo im Speicherbereich der ausführbaren Datei angegeben ist.|

## <a name="remarks"></a>Hinweise
 Diese Schnittstelle wird vom Dia-Code zum Abrufen von Informationen über die ausführbare Datei aufgerufen, um eine Liste von Stapel Rahmen während der Programmausführung zu erstellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Eine Client Anwendung implementiert diese Schnittstelle, um das Durchlaufen des Stapels während der Programmausführung zu unterstützen Eine Instanz dieser Schnittstelle wird an die Methoden [IDiaStackWalker:: getenumschlag](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) oder [IDiaStackWalker:: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) übermittelt.

## <a name="requirements"></a>Anforderungen
 Header: Dia2.h

 Bibliothek: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [SymTagEnum-Enumeration](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)
---
title: IDiaAddressMap | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e06acf045ce1893762d5c898752dd6bc40de50a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744993"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Bietet die Kontrolle darüber, wie die Dia SDK virtuelle und relative virtuelle Adressen für Debug-Objekte berechnet.

## <a name="syntax"></a>Syntax

```
IDiaAddressMap : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von `IDiaAddressMap` aufgeführt.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Gibt an, ob eine Adress Zuordnung für eine bestimmte Sitzung eingerichtet wurde.|
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Gibt an, ob die Adress Zuordnung zum Übersetzen von Symbol Adressen verwendet werden soll.|
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Gibt an, ob die Berechnung und Verwendung von relativen virtuellen Adressen aktiviert ist.|
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Ermöglicht dem Client, die Berechnung relativer virtueller Adressen zu aktivieren oder zu deaktivieren.|
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Ruft die aktuelle Bild Ausrichtung ab.|
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Legt die Bild Ausrichtung fest.|
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Legt Bild Header fest, um die Übersetzung relativer virtueller Adressen zu ermöglichen.|
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Stellt eine Adress Zuordnung zur Unterstützung von Bild layoutübersetzungen bereit.|

## <a name="remarks"></a>Hinweise
 Das Steuerelement, das von dieser Schnittstelle bereitgestellt wird, wird in zwei von Ihnen bereitgestellten Datensätzen gekapselt: Bild Header und Adress Die meisten Clients verwenden die [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) -Methode, um die richtigen Debuginformationen für ein Image zu finden, und die Methode kann normalerweise alle erforderlichen Header ermitteln und Daten selbst zuordnen. Einige Clients implementieren jedoch eine spezielle Verarbeitung und suchen nach Daten. Diese Clients verwenden die Methoden der `IDiaAddressMap` Schnittstelle, um die Dia SDK mit den Suchergebnissen bereitzustellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle ist über das Dia-Sitzungs Objekt verfügbar. Der Client ruft die `QueryInterface`-Methode auf der Dia Session Object-Schnittstelle (normalerweise [IDiaSession](../../debugger/debug-interface-access/idiasession.md)) auf, um die `IDiaAddressMap`-Schnittstelle abzurufen.

## <a name="requirements"></a>Anforderungen
 Header: Dia2.h

 Bibliothek: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
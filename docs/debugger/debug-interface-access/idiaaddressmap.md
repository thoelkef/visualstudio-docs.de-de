---
title: IDiaAddressMap | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07083ce54496992156103c58c5428cedbd321b83
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
Stellt die steuern, wie das DIA SDK virtuelle als auch für relative virtuelle Adressen für Debug-Objekte berechnet.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDiaAddressMap`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Gibt an, ob eine Adresszuordnung für eine bestimmte Sitzung eingerichtet wurde.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Gibt an, ob die-Adresszuordnung zum Übersetzen Symbol Adressen verwendet werden soll.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Gibt an, ob die Berechnung und die Verwendung der relativen virtuellen Adressen aktiviert ist.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Ermöglicht dem Client aktivieren oder Deaktivieren der Berechnung der relativen virtuellen Adressen.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Ruft die aktuelle Ausrichtung des Bilds ab.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Legt die Ausrichtung des Bilds an.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Legt image-Header, um die Übersetzung der relativen virtuellen Adressen zu aktivieren.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Stellt eine Adresse-Karte, um das Image Layout Übersetzungen unterstützen.|  
  
## <a name="remarks"></a>Hinweise  
 Das Steuerelement bereitgestellt, die von dieser Schnittstelle in zwei Sätze von Daten, die Sie angeben, gekapselt: image Header und Zuordnungen zu beheben. Die meisten Clients verwenden die [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode, um die richtige Debuginformationen zu ermitteln, für ein Bild und die Methode in der Regel alle erforderlichen Header und Karten Daten selbst ermitteln können. Implementieren jedoch einige Clients spezielle Verarbeitung und die Suche nach Daten. Solche Clients verwenden die Methoden der `IDiaAddressMap` Schnittstelle, um das DIA SDK mit den Suchergebnissen bereitzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle ist über das Sitzungsobjekt DIA verfügbar. Der Client Ruft die `QueryInterface` Methode DIA Sitzung Objektschnittstelle, in der Regel [IDiaSession](../../debugger/debug-interface-access/idiasession.md), zum Abrufen der `IDiaAddressMap` Schnittstelle.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: "MSDIA80.dll"  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
---
title: IDiaAddressMap | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 041b784154ef5c95f75d8574700a65460a0ec663
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51722725"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ermöglicht die Steuerung über die wie die DIA-SDK für virtuelle und relative virtuelle Adressen für Debug-Objekte berechnet.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDiaAddressMap`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Gibt an, ob eine Adresszuordnung für eine bestimmte Sitzung eingerichtet wurde.|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Gibt an, ob die Adresszuordnung verwendet werden soll, um Symbol Adressen zu übersetzen.|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Gibt an, ob die Berechnung und Verwenden der relativen virtuellen Adressen aktiviert ist.|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Ermöglicht dem Client aktivieren oder deaktivieren die Berechnung der relativen virtuellen Adressen.|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Ruft die Ausrichtung für das aktuelle ab.|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Legt die Ausrichtung fest.|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Legt image-Header, um die Übersetzung der relativen virtuellen Adressen zu aktivieren.|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Stellt eine Adresszuordnung zum Unterstützen von Bild Layout Übersetzungen bereit.|  
  
## <a name="remarks"></a>Hinweise  
 Die Kontrolle von dieser Schnittstelle in zwei Sätze von Daten, die Sie angeben, gekapselt: Header Bild aus, und Adressieren von Zuordnungen. Die meisten Clients verwenden die [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) Methode, um die richtige Debuginformationen zu ermitteln, für ein Bild und die Methode in der Regel alle notwendigen Header und Zuordnungen Daten selbst ermitteln können. Implementieren einige Clients jedoch spezielle Verarbeitung und die Suche nach Daten. Solche Clients verwenden die Methoden der `IDiaAddressMap` Schnittstelle, um die DIA-SDK mit den Suchergebnissen bereitzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle ist über das DIA-Sitzungsobjekt verfügbar. Der Client Ruft die `QueryInterface` Methode DIA Sitzung-Objekt-Schnittstelle, in der Regel [IDiaSession](../../debugger/debug-interface-access/idiasession.md), zum Abrufen der `IDiaAddressMap` Schnittstelle.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLL: "MSDIA80.dll"  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)




---
title: IDiaAddressMap | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 012d6b1ca06b06f56239048fee712d898a79efa9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547506"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bietet die Kontrolle darüber, wie die Dia SDK virtuelle und relative virtuelle Adressen für Debug-Objekte berechnet.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDiaAddressMap` .  
  
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
  
## <a name="remarks"></a>Bemerkungen  
 Das Steuerelement, das von dieser Schnittstelle bereitgestellt wird, wird in zwei von Ihnen bereitgestellten Datensätzen gekapselt: Bild Header und Adress Die meisten Clients verwenden die [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) -Methode, um die richtigen Debuginformationen für ein Image zu finden, und die Methode kann normalerweise alle erforderlichen Header ermitteln und Daten selbst zuordnen. Einige Clients implementieren jedoch eine spezielle Verarbeitung und suchen nach Daten. Diese Clients verwenden die Methoden der- `IDiaAddressMap` Schnittstelle, um die Dia SDK den Suchergebnissen bereitzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle ist über das Dia-Sitzungs Objekt verfügbar. Der Client ruft die-Methode für die `QueryInterface` Dia Session Object-Schnittstelle auf, normalerweise [IDiaSession](../../debugger/debug-interface-access/idiasession.md), um die- `IDiaAddressMap` Schnittstelle abzurufen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)

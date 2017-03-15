---
title: "IDiaAddressMap | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaAddressMap-Schnittstelle"
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaAddressMap
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Stellt Steuerelement darüber, wie das DIA SDK die virtuellen und relativen virtuellen Adressen für die Objekte berechnet.  
  
## Syntax  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaAddressMap`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaAddressMap::get\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|Gibt an, ob eine Adressumsetzung für eine bestimmte Sitzung eingerichtet wurde.|  
|[IDiaAddressMap::put\_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|Gibt an, ob die Adressumsetzung verwendet werden soll, um Symbol adressen zu übersetzen.|  
|[IDiaAddressMap::get\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|Gibt an, ob die Berechnung und der Verwendung von relativen virtuellen Adressen aktiviert ist.|  
|[IDiaAddressMap::put\_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|Ermöglicht dem Client, um die Berechnung von relativen virtuellen Adressen zu aktivieren oder zu deaktivieren.|  
|[IDiaAddressMap::get\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|Ruft die aktuelle Ausrichtung des Bilds ab oder legt diese fest.|  
|[IDiaAddressMap::put\_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|Legt die Ausrichtung des Bilds fest.|  
|[IDiaAddressMap::set\_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|Legt Header des Bilds fest, um die Übersetzung von relativen virtuellen Adressen zu aktivieren.|  
|[IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|Stellt eine Adressumsetzung zum Unterstützen von übersetzungen Lay\-out Bild bereit.|  
  
## Hinweise  
 Das Steuerelement, das von dieser Schnittstelle bereitgestellt wird, wird in zwei Sätzen von Daten gekapselt, die Sie bereitstellen: Adressumsetzungen und Header des Bilds.  Die meisten Clients verwenden die [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)\-Methode, um die richtigen Debuginformationen für ein Bild zu suchen und die Methode kann alle notwendigen Header und Karten von Daten in der Regel selbst ermitteln.  Die spezialisierte Implementieren von mehreren Clients das Verarbeiten und die Suche nach Daten.  Solche Clients verwenden die Methoden der Schnittstelle, um das `IDiaAddressMap` DIA SDK mit den Suchergebnissen bereitzustellen.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle ist vom Durchmesser\-Sitzungsobjekt verfügbar.  Der Client ruft die `QueryInterface`\-Methode auf Durchmesser\-Sitzungsobjekt Oberfläche, normalerweise [IDiaSession](../../debugger/debug-interface-access/idiasession.md)auf, um die `IDiaAddressMap`\-Schnittstelle abzurufen.  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
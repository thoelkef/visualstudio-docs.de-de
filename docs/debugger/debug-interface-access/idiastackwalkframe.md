---
title: "IDiaStackWalkFrame | Microsoft Docs"
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
  - "IDiaStackWalkFrame-Schnittstelle"
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaStackWalkFrame
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Behält Stapel Elementkontext zwischen den Aufrufen der [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)\-Methode bei.  
  
## Syntax  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaStackWalkFrame`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaStackWalkFrame::get\_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Ruft den Wert eines Registers ab.|  
|[IDiaStackWalkFrame::put\_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Legt den Wert eines Registers festgelegt.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Liest Speicher im Abbild.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Sucht den angegebenen Stapelrahmen für die nächste Funktion rückgabeadresse.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Sucht den angegebenen Stapelrahmen für eine Rückgabeadresse nah an der angegebenen Adresse.|  
  
## Hinweise  
 Diese Schnittstelle wird während der Programmausführung zum Lesen und Schreiben von Registern sowie Informationen über Zugriffsdatum und \- arbeitsspeicher\- Suchen rückgabeadressen.  
  
## Hinweise für Aufrufer  
 Die Clientanwendung implementiert diese Schnittstelle und führt eine Instanz der Schnittstelle zur [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)\-Methode.  Die gleiche Instanz dieser Schnittstelle wird immer wieder verwendet, um den Zustand der Register bei jedem Aufruf der `execute`\-Methode aufrechtzuerhalten.  Die `execute`\-Methode verwendet ebenfalls diese Schnittstelle, um die Rückgabeadresse zu bestimmen.  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)
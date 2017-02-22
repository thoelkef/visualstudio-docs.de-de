---
title: "IDiaStackWalkHelper | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackWalkHelper2-Schnittstelle"
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Erleichtert, den Stapel mit der Datenbank der Datei Debuggen des Programms durchlaufen \(.pdb\).  
  
## Syntax  
  
```  
  
IDiaStackWalkHelper: IUnknown  
  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaStackWalkHelper`an:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaStackWalkHelper::get\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Ruft den Wert eines Registers ab.|  
|[IDiaStackWalkHelper::put\_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Legt den Wert eines Registers festgelegt.|  
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Liest einen Block von Daten aus dem Bild der ausführbaren Datei im Arbeitsspeicher.|  
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Sucht den angegebenen Stapelrahmen für die nächste Funktion rückgabeadresse.|  
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Sucht den angegebenen Stapelrahmen für eine Rückgabeadresse nah an der angegebenen Stapeladresse.|  
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Ruft den Stapelrahmen ab, der die angegebene virtuelle Adresse enthält.|  
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Ruft das Symbol ab, das die angegebene virtuelle Adresse enthält. **Note:**  Symbol muss den Typ `SymTagFunctionType` \(ein Wert aus der [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)\-Enumeration\) verfügen.|  
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Gibt den PDATA\-Bezugspunkt Datenbindungsausdrücken zurück, der dem angegebenen virtuellen Adresse zugeordnet ist.|  
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Ruft die beginnen virtuelle Adresse eines ausführbaren ab, wenn eine virtuelle Adresse irgendwo im Speicherbereich der ausführbaren Datei.|  
  
## Hinweise  
 Diese Schnittstelle wird durch den Aufruf Durchmesser\-Code zum Abrufen von Informationen über die ausführbare Datei, um eine Liste der Stapelrahmen während der Programmausführung zu erstellen.  
  
## Hinweise für Aufrufer  
 Eine Clientanwendung implementiert diese Schnittstelle, um das Durchlaufen des Stapels während der Programmausführung zu unterstützen.  Eine Instanz dieser Schnittstelle wird an [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) oder [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)\-Methode übergeben.  
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [SymTagEnum\-Enumeration](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)   
 [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)
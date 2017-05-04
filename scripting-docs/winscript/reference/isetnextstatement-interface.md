---
title: "ISetNextStatement-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# ISetNextStatement-Schnittstelle
Diese Schnittstelle wird von einem Interpreter implementiert, um dem Prozessdebug\-Manager zu ermöglichen, die aktuelle Anweisung zu aktualisieren.  Sie wird von einem Stapelrahmenobjekt implementiert, und das PDM erhält diese Schnittstelle durch QueryInterface.  
  
 Schnittstelle stellt Methoden bereit, die zum Festlegen des Ausführungspunkts hilfreich sind, der die nächste auszuführende Anweisung bestimmt werden.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `ISetNextStatement`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Bestimmt, ob sich der Ausführungspunkt festgelegt werden kann der angegebenen Position.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Legt den Ausführungspunkt in angegebenen Position fest.|
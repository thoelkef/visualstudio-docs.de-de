---
title: "IDebugExpression-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugExpression-Schnittstelle"
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression-Schnittstelle
Stellt einen asynchron ausgewerteten Ausdruck dar.  Skriptmodule implementieren normalerweise diese Schnittstelle.  Ein Debugger IDE verwendet in der Regel diese Schnittstelle, um ein direktes Ausführungsfenster oder \-Überwachungsfenster zu aktivieren.  
  
> [!NOTE]
>  Die `IDebugExpression`\-Schnittstelle ist nur von einem Stapelrahmen verfügbar.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugExpression`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Startet die Auswertung des Ausdrucks.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Bricht den Ausdruck ab.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Bestimmt, ob der Vorgang abgeschlossen ist.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Gibt das Ergebnis der Ausdrucksauswertung als Zeichenfolge und der Rückgabewert des Vorgangs zurück.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Gibt das Ergebnis der Ausdrucksauswertung als Eigenschaft Debug\- und der Rückgabewert des Vorgangs zurück.|
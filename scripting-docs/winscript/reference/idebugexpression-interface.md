---
title: IDebugExpression-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugExpression interface
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39e139e09362fc392d1110e26837c52fd4c642c4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpression-interface"></a>IDebugExpression-Schnittstelle
Stellt einen asynchron ausgewerteten Ausdruck. Script-Module in der Regel implementieren Sie diese Schnittstelle. Ein Debugger IDE mithilfe dieser Schnittstelle in der Regel eine unmittelbare Ausführung Fenster aktivieren oder Überwachung (Fenster).  
  
> [!NOTE]
>  Die `IDebugExpression` Schnittstelle ist nur über einen Stapelrahmen verfügbar.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugExpression` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|Beginnt die Auswertung des Ausdrucks an.|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|Bricht den Ausdruck ab.|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|Bestimmt, ob der Vorgang abgeschlossen ist.|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|Gibt das Ergebnis der Auswertung von Ausdrücken als eine Zeichenfolge und der Rückgabewert des Vorgangs zurück.|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|Gibt das Ergebnis der Auswertung von Ausdrücken als eine Debugeigenschaft und der Rückgabewert des Vorgangs zurück.|
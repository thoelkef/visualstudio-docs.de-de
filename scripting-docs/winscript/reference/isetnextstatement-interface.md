---
title: ISetNextStatement-Schnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bdd71a427a8ef2c57684eef75a044d0cedf42415
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733620"
---
# <a name="isetnextstatement-interface"></a>ISetNextStatement-Schnittstelle
Diese Schnittstelle wird durch ein Interpreter ermöglichen dem Prozess Debuggen-Manager beim Aktualisieren der aktuellen Anweisung implementiert. Sie wird aus einem Stack-Frame-Objekt implementiert, und die PDM erhält diese Schnittstelle über QueryInterface.  
  
 Schnittstelle bietet Methoden, die eignen sich zum Festlegen des Ausführungspunkts, die festlegt, die nächste Anweisung ausgeführt werden.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `ISetNextStatement` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Bestimmt, ob der Ausführungspunkt an den angegebenen Speicherort festgelegt werden kann.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Legt den Ausführungspunkt am angegebenen Speicherort.|
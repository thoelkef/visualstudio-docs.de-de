---
title: ISetNextStatement-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de300a7af8492e6431f6b8513cde84a15895ad96
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786307"
---
# <a name="isetnextstatement-interface"></a>ISetNextStatement-Schnittstelle
Diese Schnittstelle wird von einem Interpreter, um den prozessbasierten Debugmanager zum Aktualisieren der aktuellen Anweisung zu ermöglichen, implementiert. Sie wird aus einem Stapel-Frame-Objekt implementiert, und das PDM erhält, diese Schnittstelle über QueryInterface.  
  
 Schnittstelle bietet Methoden, die nützlich für das Festlegen des Ausführungspunkts, der bestimmt, die nächste Anweisung ausgeführt werden.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `ISetNextStatement` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Bestimmt, ob es sich bei der Ausführungspunkt zu einem angegebenen Speicherort festgelegt werden kann.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Legt den Ausführungspunkt an der angegebenen Position fest.|
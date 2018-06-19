---
title: IActiveScriptParseProcedure32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 8cd253db8cb63adad093b84c4bf47df07bd66d69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645870"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Wenn das Windows-Skriptmodul des Quelltexts Code, Prozeduren, die das Skript hinzugefügt werden kann, implementiert die `IActiveScriptParseProcedure32` Schnittstelle. Für interpretierte Skriptsprachen, die über keine unabhängig erstellungsumgebung, z. B. VBScript, stellt dies einen alternativen Mechanismus (außer `IActiveScriptParse32` oder `IPersist`*) Skript Prozeduren auf den Namespace hinzufügen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|||  
|-|-|  
|Methode|Beschreibung|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Die Prozedur angegebenen Code analysiert, und fügt die Prozedur auf den Namespace.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)
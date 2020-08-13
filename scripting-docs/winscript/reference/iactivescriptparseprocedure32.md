---
title: IActiveScriptParseProcedure32 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 71a22f422ff04e56a7aaa7a715641d190ade47bf
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144388"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Wenn die Windows Script-Engine zulässt, dass dem Skript der Quellcode Text für Prozeduren hinzugefügt wird, wird die- `IActiveScriptParseProcedure32` Schnittstelle implementiert. Bei interpretierten Skriptsprachen, die keine unabhängige Erstellungs Umgebung haben (z. b. VBScript), bietet dies einen alternativen Mechanismus (außer `IActiveScriptParse32` oder `IPersist` *), um dem Namespace Skript Prozeduren hinzuzufügen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|BESCHREIBUNG|
|-|-|
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analysiert die angegebene Code Prozedur und fügt die Prozedur zum-Namespace hinzu.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)
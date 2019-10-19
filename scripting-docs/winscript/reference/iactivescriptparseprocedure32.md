---
title: IActiveScriptParseProcedure32 | Microsoft-Dokumentation
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
ms.openlocfilehash: 1993cbef966a4d73a2a3ed55c3317db444702232
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574879"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
Wenn die Windows Script-Engine zulässt, dass dem Skript der Quellcode Text für Prozeduren hinzugefügt wird, wird die `IActiveScriptParseProcedure32`-Schnittstelle implementiert. Bei interpretierten Skriptsprachen, die keine unabhängige Erstellungs Umgebung haben (z. b. VBScript), bietet dies einen alternativen Mechanismus (außer `IActiveScriptParse32` oder `IPersist` *), um dem Namespace Skript Prozeduren hinzuzufügen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|||  
|-|-|  
|Methode|Beschreibung|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|Analysiert die angegebene Code Prozedur und fügt die Prozedur zum-Namespace hinzu.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)
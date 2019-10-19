---
title: Iactivescriptanalyse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81f64352c15dce233058d49b70e35da7e2238688
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561642"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Wenn die Windows-Skript-Engine das Hinzufügen von rohtextcode-Skriptlets zum Skript zulässt oder das Auswerten von Ausdrucks Text zur Laufzeit zulässt, wird die `IActiveScriptParse`-Schnittstelle implementiert. Bei interpretierten Skriptsprachen, die keine unabhängige Erstellungs Umgebung haben (z. b. VBScript), stellt dies einen alternativen Mechanismus (außer `IPersist*`) zum erhalten von Skriptcode in der Skript-Engine und zum Anfügen von Skript Fragmenten an verschiedene Objekt Ereignisse bereit. .  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Initialisiert die Skript-Engine.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Fügt dem Skript ein Code-Scriptlet hinzu.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analysiert das angegebene Code-Scriptlet, fügt dem Namespace Deklarationen hinzu und wertet Code entsprechend aus.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)
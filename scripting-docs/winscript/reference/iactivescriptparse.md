---
title: IActiveScriptParse | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0e3990ca43043909d99b309f58a344c1727450
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Wenn die Windows Script Engine ermöglicht unformatierten Text Code Skriptlets das Skript hinzugefügt werden oder Ausdruckstext zur Laufzeit ausgewertet werden, implementiert die `IActiveScriptParse` Schnittstelle. Für interpretierte Skriptsprachen, die über keine unabhängig erstellungsumgebung, z. B. VBScript, stellt dies einen alternativen Mechanismus (außer `IPersist*`) Skriptcode in das Skriptmodul abgerufen und Skriptfragmente an verschiedenen Objekt anzufügen Ereignisse.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Initialisiert das Skriptmodul.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Das Skript wird ein Code-Scriptlet hinzugefügt.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analysiert den angegebenen Code-Scriptlet, Deklarationen in den Namespace hinzufügen und Auswerten von Code nach Bedarf.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)
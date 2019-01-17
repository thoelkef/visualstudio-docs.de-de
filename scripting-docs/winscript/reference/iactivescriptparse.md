---
title: IActiveScriptParse | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 8325ffcb21f1871ca742611e6587df02ef3b89c8
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349009"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Wenn das Windows-Skript-Engine Rohtext Code Skriptlets das Skript hinzugefügt werden kann oder Text des Ausdrucks zur Laufzeit ausgewertet werden kann, implementiert die `IActiveScriptParse` Schnittstelle. Für interpretierte Skriptsprachen, die keine unabhängige erstellungsumgebung, z. B. VBScript, stellt dies einen alternativen Mechanismus (außer `IPersist*`) zu Skriptcode in der Skript-Engine abrufen und Skriptfragmente an verschiedenen Objekt anzufügen Ereignisse.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|Initialisiert die Skript-Engine.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|Das Skript wird ein Code-Scriptlet hinzugefügt.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|Analysiert den angegebenen Code-Scriptlet, Deklarationen in den Namespace hinzufügen und die Bewertung von Code nach Bedarf.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Schnittstellen](../../winscript/reference/active-script-interfaces.md)
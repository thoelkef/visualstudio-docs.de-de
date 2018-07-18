---
title: IActiveScriptParse32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 688a89515179912c1ed3ac815f0febf50ab4db0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724400"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Wenn die Windows Script Engine ermöglicht unformatierten Text Code Skriptlets das Skript hinzugefügt werden oder Ausdruckstext zur Laufzeit ausgewertet werden, implementiert die `IActiveScriptParse32` Schnittstelle. Für interpretierte Skriptsprachen, die über keine unabhängig erstellungsumgebung, z. B. VBScript, stellt dies einen alternativen Mechanismus (außer `IPersist*`) Skriptcode in das Skriptmodul abgerufen und Skriptfragmente an verschiedenen Objekt anzufügen Ereignisse.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Das Skript wird ein Code-Scriptlet hinzugefügt.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Initialisiert das Skriptmodul.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Analysiert den angegebenen Code-Scriptlet, Deklarationen in den Namespace hinzufügen und Auswerten von Code nach Bedarf.|
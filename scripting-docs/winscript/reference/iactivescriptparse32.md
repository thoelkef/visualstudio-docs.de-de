---
title: IActiveScriptParse32 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 568feacfe75de22a330c892a44fa4f4f6fd0e3b8
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835315"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Wenn die Windows-Skript-Engine das Hinzufügen von rohtextcode-Skriptlets zum Skript zulässt oder das Auswerten von Ausdrucks Text zur Laufzeit zulässt, wird die- `IActiveScriptParse32` Schnittstelle implementiert. Bei interpretierten Skriptsprachen, die keine unabhängige Erstellungs Umgebung haben (z. b. VBScript), stellt dies einen alternativen Mechanismus (außer) bereit, `IPersist*` um Skriptcode in die Skript-Engine zu übernehmen und Skript Fragmente an verschiedene Objekt Ereignisse anzufügen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Fügt dem Skript ein Code-Scriptlet hinzu.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Initialisiert die Skript-Engine.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Analysiert das angegebene Code-Scriptlet, fügt dem Namespace Deklarationen hinzu und wertet Code entsprechend aus.|
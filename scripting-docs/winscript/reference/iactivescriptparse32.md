---
title: IActiveScriptParse32 | Microsoft-Dokumentation
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
ms.openlocfilehash: 9f44239b4e423588b8455b93b87e4084a9c7d1c4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347644"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Wenn das Windows-Skript-Engine Rohtext Code Skriptlets das Skript hinzugefügt werden kann oder Text des Ausdrucks zur Laufzeit ausgewertet werden kann, implementiert die `IActiveScriptParse32` Schnittstelle. Für interpretierte Skriptsprachen, die keine unabhängige erstellungsumgebung, z. B. VBScript, stellt dies einen alternativen Mechanismus (außer `IPersist*`) zu Skriptcode in der Skript-Engine abrufen und Skriptfragmente an verschiedenen Objekt anzufügen Ereignisse.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|Das Skript wird ein Code-Scriptlet hinzugefügt.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|Initialisiert die Skript-Engine.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|Analysiert den angegebenen Code-Scriptlet, Deklarationen in den Namespace hinzufügen und die Bewertung von Code nach Bedarf.|
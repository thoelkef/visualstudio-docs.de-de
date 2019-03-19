---
title: IActiveScriptDebug-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6341b5c3763d6e4c836b3bdc0539552fcbe7f980
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58151023"
---
# <a name="iactivescriptdebug-interface"></a>IActiveScriptDebug-Schnittstelle
Implementiert, indem die Skript-Engines, unterstützen das Debuggen. In der Regel auf ein Objekt, implementiert die `IActiveScriptDebug` -Schnittstelle auch implementiert die `IActiveScript` Schnittstelle. Wenn dies der Fall ist, rufen Sie die `IActiveScript::QueryInterface` Methode zum Abrufen der `IActiveScriptDebug` Schnittstelle.  
  
 Die `IActiveScriptDebug` Schnittstelle stellt die Möglichkeiten für:  
  
- Smarthosts dokumentverwaltung übernehmen.  
  
- Prozessbasierter Debug-Manager zu synchronisieren, Debuggen von mehreren Skript-Engines.  
  
  Zusätzlich zu den von geerbten Methoden `IUnknown`, `IActiveScriptDebug` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Gibt den Textattribute für ein beliebiger Speicherblock, der Skripttext zurück.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Gibt den Textattribute für eine beliebige Scriptlet zurück.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Delegiert an `IDebugDocumentContext::EnumCodeContexts`.|
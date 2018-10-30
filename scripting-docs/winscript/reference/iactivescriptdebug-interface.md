---
title: IActiveScriptDebug-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0e21f4c99da886bc4907acf8b0934e1b46d57689
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942087"
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
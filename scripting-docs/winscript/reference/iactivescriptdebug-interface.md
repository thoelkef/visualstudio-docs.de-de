---
title: IActiveScriptDebug-Schnittstelle | Microsoft Docs
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
ms.openlocfilehash: a1e1d0c1cf51c63f1bb3fcd90ae72520da907e50
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645820"
---
# <a name="iactivescriptdebug-interface"></a>IActiveScriptDebug-Schnittstelle
Implementiert, indem Script-Module, unterstützen das Debuggen. In der Regel ein Objekt, implementiert die `IActiveScriptDebug` Schnittstelle auch implementiert die `IActiveScript` Schnittstelle. Wenn dies der Fall ist, rufen Sie die `IActiveScript::QueryInterface` Methode zum Abrufen der `IActiveScriptDebug` Schnittstelle.  
  
 Die `IActiveScriptDebug` Schnittstelle bietet die notwendigen Mittel zum:  
  
-   Smarthosts Dokumentverwaltungsfunktionen übernehmen.  
  
-   Prozess-Debug-Manager mit dem Debuggen von mehreren Skriptmodule synchronisiert.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IActiveScriptDebug` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|Gibt die Textattribute für einen beliebigen TextBlock Skript.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|Gibt den Textattribute für eine beliebige Scriptlet zurück.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|Delegiert an `IDebugDocumentContext::EnumCodeContexts`.|
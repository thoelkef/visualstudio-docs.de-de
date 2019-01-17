---
title: IActiveScriptSiteDebug-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 339325686d2a98e34c6e9f96056612769a9e110e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348307"
---
# <a name="iactivescriptsitedebug-interface"></a>IActiveScriptSiteDebug-Schnittstelle
Implementieren von Smart Hosts die `IActiveScriptSiteDebug` Benutzeroberfläche, die dokumentverwaltung ausführen und Debuggen teilnehmen. Die `IActiveScriptSite` Objekt in der Regel stellt eine Implementierung der `IActiveScriptSiteDebug` Schnittstelle. Wenn dies geschehen ist, rufen Sie die `IActiveScriptSite::QueryInterface` Methode zum Abrufen der `IActiveScriptSiteDebug` Schnittstelle.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IActiveScriptSiteDebug` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Die Sprach-Engine, die für die Delegieren `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Gibt zurück, das Debug-Application-Objekt mit diesem Skript Standort verbunden ist.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Ruft den Anwendungsknoten in dem Script Dokumente hinzugefügt werden soll.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Ermöglicht einen Smarthost zu bestimmen, wie zum Behandeln von Laufzeitfehlern führen.|
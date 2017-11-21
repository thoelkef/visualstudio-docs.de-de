---
title: IActiveScriptSiteDebug-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9b36054deeceb0528fb7ea399cc41d8edbbb47e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug-interface"></a>IActiveScriptSiteDebug-Schnittstelle
Smarthosts implementieren die `IActiveScriptSiteDebug` Schnittstelle Dokumentverwaltungsfunktionen ausführen und Debuggen teilnehmen. Die `IActiveScriptSite` Objekt in der Regel stellt eine Implementierung der `IActiveScriptSiteDebug` Schnittstelle. Wenn dies geschehen ist, rufen Sie die `IActiveScriptSite::QueryInterface` Methode zum Abrufen der `IActiveScriptSiteDebug` Schnittstelle.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IActiveScriptSiteDebug` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Durch das Sprachmodul zum Delegieren verwendet `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Gibt die Debug-Application-Objekt mit diesem Skript-Site verknüpft sind.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Ruft den Anwendungsknoten unter dem Script Dokumenten hinzugefügt werden soll.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Ermöglicht einen smart Host kann bestimmen, wie zur Laufzeit Fehler behandelt.|
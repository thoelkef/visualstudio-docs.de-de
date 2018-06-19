---
title: IActiveScriptSiteDebug32 Schnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: a752851aa6afd903747dc58fed79d2bc5b27e3e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725120"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32-Schnittstelle
Smarthosts implementieren die `IActiveScriptSiteDebug32` Schnittstelle Dokumentverwaltungsfunktionen ausführen und Debuggen teilnehmen. Die `IActiveScriptSite` Objekt in der Regel stellt eine Implementierung der `IActiveScriptSiteDebug32` Schnittstelle. Wenn dies geschehen ist, rufen Sie die `IActiveScriptSite::QueryInterface` Methode zum Abrufen der `IActiveScriptSiteDebug32` Schnittstelle.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IActiveScriptSiteDebug32` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Gibt die Debug-Application-Objekt mit diesem Skript-Site verknüpft sind.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Durch das Sprachmodul zum Delegieren verwendet `IDebugCodeContext::GetSourceContext`.|
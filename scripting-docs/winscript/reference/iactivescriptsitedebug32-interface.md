---
title: IActiveScriptSiteDebug32-Schnittstelle | Microsoft-Dokumentation
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
ms.openlocfilehash: e7937311e01274570e34bd639a0dc5f68206a3aa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992444"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32-Schnittstelle
Implementieren von Smart Hosts die `IActiveScriptSiteDebug32` Benutzeroberfläche, die dokumentverwaltung ausführen und Debuggen teilnehmen. Die `IActiveScriptSite` Objekt in der Regel stellt eine Implementierung der `IActiveScriptSiteDebug32` Schnittstelle. Wenn dies geschehen ist, rufen Sie die `IActiveScriptSite::QueryInterface` Methode zum Abrufen der `IActiveScriptSiteDebug32` Schnittstelle.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IActiveScriptSiteDebug32` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Gibt zurück, das Debug-Application-Objekt mit diesem Skript Standort verbunden ist.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Die Sprach-Engine, die für die Delegieren `IDebugCodeContext::GetSourceContext`.|
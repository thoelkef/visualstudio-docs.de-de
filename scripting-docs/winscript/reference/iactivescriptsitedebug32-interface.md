---
title: IActiveScriptSiteDebug32-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 2a55161f76fcd98b52ddb769c640aca0e903239b
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835263"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32-Schnittstelle
Smarthosts implementieren die `IActiveScriptSiteDebug32` -Schnittstelle zum Durchführen der Dokument Verwaltung und zum Debuggen. Das- `IActiveScriptSite` Objekt stellt in der Regel eine Implementierung der- `IActiveScriptSiteDebug32` Schnittstelle bereit. Wenn dies geschehen ist, rufen Sie die- `IActiveScriptSite::QueryInterface` Methode auf, um die- `IActiveScriptSiteDebug32` Schnittstelle abzurufen.  
  
 Zusätzlich zu den von geerbten Methoden macht `IUnknown` die- `IActiveScriptSiteDebug32` Schnittstelle die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|Gibt das Debug-Anwendungs Objekt zurück, das dieser Skript Site zugeordnet ist.|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|Wird von der Sprach-Engine zum Delegieren verwendet `IDebugCodeContext::GetSourceContext` .|
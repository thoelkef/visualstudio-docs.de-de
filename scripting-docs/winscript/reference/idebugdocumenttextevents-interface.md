---
title: IDebugDocumentTextEvents-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4329af4e440eb9ee0de57a64e6ab55b48b6375b4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150412"
---
# <a name="idebugdocumenttextevents-interface"></a>IDebugDocumentTextEvents-Schnittstelle
Stellt Ereignisse bereit, die auf Änderungen am zugehörigen Textdokument hinweisen.  
  
> [!NOTE]
>  Text des Dokuments ändert, wenn die Ereignisse auf diesem Fire-Schnittstelle. Ereignishandler können rufen Sie den neuen Text mithilfe der `IDebugDocumentText` Schnittstelle.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugDocumentTextEvents` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Gibt an, dass das zugrunde liegende Dokument wurde gelöscht, und nicht mehr gültig ist|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Gibt an, dass der neuer Text zum Dokument hinzugefügt wurde|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Gibt an, dass Text aus dem Dokument entfernt wurde.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Gibt an, dass Text ersetzt wurde.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Gibt an, dass der Bereich der zugrunde liegenden Position zugeordnete Textattribute geändert haben.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Gibt an, dass die Dokumentattribute geändert.|
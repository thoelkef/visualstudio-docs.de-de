---
title: IDebugDocumentTextEvents-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 078cd468b64d30c20f48a3392aa4509ed054fc3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextevents-interface"></a>IDebugDocumentTextEvents-Schnittstelle
Bietet Ereignisse, die Änderungen in den zugehörigen Text-Dokument angibt.  
  
> [!NOTE]
>  Text des Dokuments ändert, wenn die Ereignisse für diese werden als Schnittstelle. Ereignishandler können rufen Sie den neuen Text mithilfe der `IDebugDocumentText` Schnittstelle.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugDocumentTextEvents` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Gibt an, dass das zugrunde liegende Dokument wurde gelöscht, und nicht mehr gültig ist|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Gibt an, dass der neue Text zum Dokument hinzugefügt wurde|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Gibt an, dass der Text aus dem Dokument entfernt wurde.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Gibt an, dass Text ersetzt wurde.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Gibt an, dass die zugrunde liegenden Zeichenbereich Position zugeordneten Textattribute geändert wurden.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Gibt an, dass das Dokumentattribute geändert.|
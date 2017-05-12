---
title: "IDebugDocumentTextEvents-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentTextEvents-Schnittstelle"
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentTextEvents-Schnittstelle
Stellt die Ereignisse bereit, die Änderungen am zugeordneten Textdokument angeben.  
  
> [!NOTE]
>  Der Dokumenttext ändert wenn die Ereignisse auf diesem Schnittstellenfeuer.  Ereignishandler wird möglicherweise den neuen Text mithilfe der `IDebugDocumentText`\-Schnittstelle ab.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugDocumentTextEvents`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Gibt, an, dass das zugrunde liegende Dokument zerstört wurde und ist nicht mehr gültig|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Gibt an, dass neuer Text zum Dokument hinzugefügt wurde|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Gibt an, dass Text aus dem Dokument entfernt wurde.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Gibt an, dass Text ersetzt wurde.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Gibt an, dass die Textattribute, die mit dem zugrunde liegenden Zeichenpositionsbereich zugeordnet werden, geändert wurden.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Gibt an, dass die Dokumentenattribute geändert haben.|
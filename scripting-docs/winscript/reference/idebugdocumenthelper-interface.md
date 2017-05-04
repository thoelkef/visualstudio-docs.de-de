---
title: "IDebugDocumentHelper-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentHelper-Schnittstelle"
ms.assetid: b652a31e-b87b-45f1-b586-94f2b6e822db
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper-Schnittstelle
Stellen Sie Implementierungen für viele Schnittstellen bereit, die für intelligente Hosting, wie `IDebugDocument`, `IDebugDocumentContext`, `IDebugDocumentProvider`, `IDebugDocumentText` und `IDebugDocumentTextEvents`\-Schnittstellen erforderlich sind.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugDocumentHelper`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugDocumentHelper::Init](../../winscript/reference/idebugdocumenthelper-init.md)|Initialisiert eine Debug\- Dokumentenhilfe mit einem Namen und zeichnet Attribute ab.|  
|[IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)|Fügt dieses Dokument der Dokumentstruktur hinzu.|  
|[IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)|Entfernt dieses Dokument von der Dokumentstruktur.|  
|[IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)|Fügt eine Unicode\-Zeichenfolge am Ende dieses Dokuments an.|  
|[IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)|Fügt eine DBCS\-Zeichenfolge am Ende dieses Dokuments an.|  
|[IDebugDocumentHelper::SetDebugDocumentHost](../../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)|Legt `IDebugDocumentHost` für dieses Dokument fest.|  
|[IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)|Benachrichtigt die Hilfe, dass der angegebene Text verfügbar ist, es bietet aber nicht die Zeichen.|  
|[IDebugDocumentHelper::DefineScriptBlock](../../winscript/reference/idebugdocumenthelper-definescriptblock.md)|Gibt die Hilfe an, dass ein bestimmter Bereich von Zeichen ein Skriptblock ist, der durch das angegebene Skriptmodul behandelt wird.|  
|[IDebugDocumentHelper::SetDefaultTextAttr](../../winscript/reference/idebugdocumenthelper-setdefaulttextattr.md)|Legt die Standardattribute fest, um für Text zu verwenden, der nicht in einem Skriptblock ist.|  
|[IDebugDocumentHelper::SetTextAttributes](../../winscript/reference/idebugdocumenthelper-settextattributes.md)|Legt die Attribute für ein Textbereich fest.|  
|[IDebugDocumentHelper::SetLongName](../../winscript/reference/idebugdocumenthelper-setlongname.md)|Legt den langen Namen für das Dokument fest.|  
|[IDebugDocumentHelper::SetShortName](../../winscript/reference/idebugdocumenthelper-setshortname.md)|Legt den Kurznamen für das Dokument fest.|  
|[IDebugDocumentHelper::SetDocumentAttr](../../winscript/reference/idebugdocumenthelper-setdocumentattr.md)|Legt die Attribute für dieses Dokument fest.|  
|[IDebugDocumentHelper::GetDebugApplicationNode](../../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)|Gibt den Debug\- Anwendungsknoten entsprechend diesem Dokument zurück.|  
|[IDebugDocumentHelper::GetScriptBlockInfo](../../winscript/reference/idebugdocumenthelper-getscriptblockinfo.md)|Ruft den Bereich von Zeichen und von Skriptmodul entsprechend einem Skriptblock ab.|  
|[IDebugDocumentHelper::CreateDebugDocumentContext](../../winscript/reference/idebugdocumenthelper-createdebugdocumentcontext.md)|Erstellt ein neues Dokumentenkontext debuggen.|  
|[IDebugDocumentHelper::BringDocumentToTop](../../winscript/reference/idebugdocumenthelper-bringdocumenttotop.md)|Setzt dieses Dokument zur oben in der Debuggerbenutzeroberfläche.|  
|[IDebugDocumentHelper::BringDocumentContextToTop](../../winscript/reference/idebugdocumenthelper-bringdocumentcontexttotop.md)|Setzt einen Kontext dieses Dokuments zur oben in der Debuggerbenutzeroberfläche.|
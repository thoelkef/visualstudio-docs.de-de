---
title: IDebugDocumentHelper-Schnittstelle | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentHelper interface
ms.assetid: b652a31e-b87b-45f1-b586-94f2b6e822db
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: baadcc1e2dba0b07e132298167b9b711e40cd912
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelper-interface"></a>IDebugDocumentHelper-Schnittstelle
Geben Sie z. B. die Implementierungen für viele Schnittstellen, die erforderlich sind, für das Hosten von intelligenten der `IDebugDocument`, `IDebugDocumentContext`, `IDebugDocumentProvider`, `IDebugDocumentText`, und `IDebugDocumentTextEvents` Schnittstellen.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugDocumentHelper` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugDocumentHelper::Init](../../winscript/reference/idebugdocumenthelper-init.md)|Initialisiert eine Debug-Dokument-Hilfsprogramm mit einem Namen und anfängliche Attribute an.|  
|[IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)|Dieses Dokument hinzugefügt zur Dokumentstruktur.|  
|[IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)|Dieses Dokument entfernt aus der Dokumentstruktur.|  
|[IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)|Fügt eine Unicode-Zeichenfolge zum Beenden dieses Dokuments.|  
|[IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)|Fügt eine DBCS-Zeichenfolge zum Beenden dieses Dokuments.|  
|[IDebugDocumentHelper::SetDebugDocumentHost](../../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)|Legt die `IDebugDocumentHost` für dieses Dokument.|  
|[IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)|Benachrichtigt, dass der angegebene Text verfügbar ist, aber es keine Zeichen bietet dem Hilfsprogramm.|  
|[IDebugDocumentHelper::DefineScriptBlock](../../winscript/reference/idebugdocumenthelper-definescriptblock.md)|Gibt an, für die Hilfe, die ein bestimmter Bereich von Zeichen ein Skriptblock, der vom Modul angegebenen Skript behandelt wird.|  
|[IDebugDocumentHelper::SetDefaultTextAttr](../../winscript/reference/idebugdocumenthelper-setdefaulttextattr.md)|Legt die Standardattribute für Text verwenden, die nicht in einem Skriptblock enthalten ist.|  
|[IDebugDocumentHelper::SetTextAttributes](../../winscript/reference/idebugdocumenthelper-settextattributes.md)|Legt die Attribute für einen Textbereich fest.|  
|[IDebugDocumentHelper::SetLongName](../../winscript/reference/idebugdocumenthelper-setlongname.md)|Legt den langen Namen für das Dokument fest.|  
|[IDebugDocumentHelper::SetShortName](../../winscript/reference/idebugdocumenthelper-setshortname.md)|Legt den kurzen Namen für das Dokument.|  
|[IDebugDocumentHelper::SetDocumentAttr](../../winscript/reference/idebugdocumenthelper-setdocumentattr.md)|Legt die Attribute für dieses Dokument fest.|  
|[IDebugDocumentHelper::GetDebugApplicationNode](../../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)|Gibt den Debugmodus Anwendungsknoten zu diesem Dokument entsprechenden zurück.|  
|[IDebugDocumentHelper::GetScriptBlockInfo](../../winscript/reference/idebugdocumenthelper-getscriptblockinfo.md)|Ruft den Bereich von Zeichen und dem Skriptmodul entspricht ein Skriptblock ab.|  
|[IDebugDocumentHelper::CreateDebugDocumentContext](../../winscript/reference/idebugdocumenthelper-createdebugdocumentcontext.md)|Erstellt einen neuen Kontext der Debug-Dokument.|  
|[IDebugDocumentHelper::BringDocumentToTop](../../winscript/reference/idebugdocumenthelper-bringdocumenttotop.md)|Schaltet dieses Dokuments nach oben im Debugger-Benutzeroberfläche.|  
|[IDebugDocumentHelper::BringDocumentContextToTop](../../winscript/reference/idebugdocumenthelper-bringdocumentcontexttotop.md)|Stellt einen Kontext dieses Dokuments oben auf der Debugger-Benutzeroberfläche.|
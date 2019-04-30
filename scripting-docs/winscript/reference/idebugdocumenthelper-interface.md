---
title: IDebugDocumentHelper-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHelper interface
ms.assetid: b652a31e-b87b-45f1-b586-94f2b6e822db
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7322ea5e2026ff3f4491ed1106dceb97a5f11c73
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000897"
---
# <a name="idebugdocumenthelper-interface"></a>IDebugDocumentHelper-Schnittstelle
Stellen Sie Implementierungen für viele Schnittstellen, die für Smarthosts, z. B. die `IDebugDocument`, `IDebugDocumentContext`, `IDebugDocumentProvider`, `IDebugDocumentText`, und `IDebugDocumentTextEvents` Schnittstellen.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugDocumentHelper` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugDocumentHelper::Init](../../winscript/reference/idebugdocumenthelper-init.md)|Initialisiert eine Debughilfe-Dokument mit einem Namen und die anfängliche Attribute.|  
|[IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)|In diesem Dokument und die Dokumentstruktur hinzugefügt.|  
|[IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)|In diesem Dokument entfernt aus der Dokumentstruktur.|  
|[IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)|Fügt eine Unicode-Zeichenfolge zum Beenden dieses Dokuments.|  
|[IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)|Fügt eine DBCS-Zeichenfolge zum Beenden dieses Dokuments.|  
|[IDebugDocumentHelper::SetDebugDocumentHost](../../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)|Legt die `IDebugDocumentHost` für dieses Dokument.|  
|[IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)|Benachrichtigt, dass der angegebene Text verfügbar ist, aber es nicht die Zeichen bietet der-Hilfe.|  
|[IDebugDocumentHelper::DefineScriptBlock](../../winscript/reference/idebugdocumenthelper-definescriptblock.md)|Gibt an, für die Hilfe, die ein bestimmter Bereich von Zeichen einen Skriptblock, der von der angegebenen Skript-Engine verarbeitet wird.|  
|[IDebugDocumentHelper::SetDefaultTextAttr](../../winscript/reference/idebugdocumenthelper-setdefaulttextattr.md)|Legt fest, die Standardattribute für Text verwendet wird, die nicht in einem Skriptblock enthalten ist.|  
|[IDebugDocumentHelper::SetTextAttributes](../../winscript/reference/idebugdocumenthelper-settextattributes.md)|Legt die Attribute für einen Textbereich fest.|  
|[IDebugDocumentHelper::SetLongName](../../winscript/reference/idebugdocumenthelper-setlongname.md)|Legt den langen Namen für das Dokument fest.|  
|[IDebugDocumentHelper::SetShortName](../../winscript/reference/idebugdocumenthelper-setshortname.md)|Legt den kurzen Namen für das Dokument fest.|  
|[IDebugDocumentHelper::SetDocumentAttr](../../winscript/reference/idebugdocumenthelper-setdocumentattr.md)|Legt die Attribute für dieses Dokument fest.|  
|[IDebugDocumentHelper::GetDebugApplicationNode](../../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)|Gibt die Knoten der Debug-Anwendung für dieses Dokument zurück.|  
|[IDebugDocumentHelper::GetScriptBlockInfo](../../winscript/reference/idebugdocumenthelper-getscriptblockinfo.md)|Ruft den Bereich von Zeichen und der Skript-Engine, die für einen Skriptblock ab.|  
|[IDebugDocumentHelper::CreateDebugDocumentContext](../../winscript/reference/idebugdocumenthelper-createdebugdocumentcontext.md)|Erstellt einen neuen Dokumentkontext für den Debugmodus.|  
|[IDebugDocumentHelper::BringDocumentToTop](../../winscript/reference/idebugdocumenthelper-bringdocumenttotop.md)|Bringt in diesem Dokument im oberen Bereich im Debugger-Benutzeroberfläche.|  
|[IDebugDocumentHelper::BringDocumentContextToTop](../../winscript/reference/idebugdocumenthelper-bringdocumentcontexttotop.md)|Bietet einen Kontext dieses Dokuments am Anfang der Debugger-Benutzeroberfläche an.|
---
title: IDebugDocumentHost-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 226e2700b471cd34496682d233e57946e124ff3b
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155666"
---
# <a name="idebugdocumenthost-interface"></a>IDebugDocumentHost-Schnittstelle
Hostspezifische Funktionen, wie z.B. Syntaxfarben, an den Debugger verfügbar gemacht. Die `IDebugDocumentHelper::SetDebugDocumentHost` Methode nimmt diese Schnittstelle als Argument.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugDocumentHost` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Gibt einen Bereich von Zeichen, die mithilfe von hinzugefügt wurden `IDebugDocumentHelper::AddDeferredText`, im ursprünglichen Hostdokument.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Gibt die Textattribute für einen Textblock Dokument zurück.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Benachrichtigt den Host, ein neuen Dokumentkontext erstellt wird, und der Host kann optional ein Objekt zurück, der den neuen Kontext steuert.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Gibt den vollständigen Pfad (einschließlich des Dateinamens) der Quelldatei des Dokuments zurück.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Gibt den Namen des Dokuments ohne Pfadinformationen.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Benachrichtigt den Host, dass die Quelldatei des Dokuments gespeichert wurde und dessen Inhalt aktualisiert werden sollen.|
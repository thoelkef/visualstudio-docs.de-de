---
title: IDebugDocumentHost-Schnittstelle | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: adaeb98f18a052106036a91885696dd4b4760dea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24726990"
---
# <a name="idebugdocumenthost-interface"></a>IDebugDocumentHost-Schnittstelle
Hostspezifische-Funktionen wie Syntaxfarben, die im Debugger verfügbar gemacht. Die `IDebugDocumentHelper::SetDebugDocumentHost` Methode nimmt diese Schnittstelle als Argument.  
  
 Zusätzlich zu den von geerbten Methoden `IUnknown`, `IDebugDocumentHost` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|Gibt einen Bereich von Zeichen, die mit hinzugefügten `IDebugDocumentHelper::AddDeferredText`, in das Originaldokument Host.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|Gibt den Textattribute für einen Textblock Dokument zurück.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|Benachrichtigt den Host, dass ein neuer Dokumentenkontext erstellt wird, und der Host kann optional ein Objekt zurückgeben, der den neuen Kontext steuert.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|Gibt den vollständigen Pfad (einschließlich des Dateinamens) der Quelldatei für das Dokument zurück.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|Gibt den Namen des Dokuments ohne Pfadinformationen zurück.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|Benachrichtigt den Host, dass das Dokument Quelldatei gespeichert wurde und dessen Inhalt aktualisiert werden sollen.|
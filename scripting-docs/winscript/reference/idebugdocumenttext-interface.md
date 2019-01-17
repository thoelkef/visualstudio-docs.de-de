---
title: IDebugDocumentText-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentText interface
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 763678b08c22fe34ec6ffebbe670fb8b50af6576
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344394"
---
# <a name="idebugdocumenttext-interface"></a>IDebugDocumentText-Schnittstelle
Bietet Zugriff auf eine reine Textversion des Debugdokuments. Diese Schnittstelle wird verwendet, die folgenden Konventionen:  
  
- Sowohl Zeichenpositionen und Zeilennummern sind nullbasiert.  
  
- Zeichenpositionen darstellen Zeichenoffsets; Sie nicht darstellen Byte oder word-Offsets. Für Win32 ist eine Zeichenposition eine Unicode-Offset.  
  
  Zusätzlich zu den von geerbten Methoden `IDebugDocument`, `IDebugDocumentText` Schnittstelle verfügbar macht, die folgenden Methoden.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|Gibt die Attribute des Dokuments zurück.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|Gibt die Anzahl der Zeilen und die Anzahl der Zeichen im Dokument zurück.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|Gibt-Position des Zeichens für das erste Zeichen einer Zeile.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|Gibt die Nummer der Zeile und optional das Zeichenoffset in der Zeile, die entspricht, der angegebenen Zeichenposition zurück.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|Ruft ab, die Zeichen bzw. eine Zeichenposition Bereich zugeordneten Zeichenformate.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|Gibt die Zeichenposition Bereich, die einem Dokumentenkontext entsprechen zurück.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|Erstellt ein Dokument Context-Objekt, dem Bereich der angegebenen Position entspricht.|
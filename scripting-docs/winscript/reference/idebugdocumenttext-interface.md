---
title: IDebugDocumentText-Schnittstelle | Microsoft Docs
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
ms.openlocfilehash: 9522d1075cd796fb69f6abbc42adc2706a817fed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727950"
---
# <a name="idebugdocumenttext-interface"></a>IDebugDocumentText-Schnittstelle
Bietet Zugriff auf eine nur-Text-Version des Dokuments Debuggen. Diese Schnittstelle wird verwendet, die folgenden Konventionen:  
  
-   Zeichenpositionen und Zeilennummern sind nullbasiert.  
  
-   Zeichenpositionen darstellen Zeichenoffsets; Sie nicht darstellen Byte oder word-Offsets. Für Win32 ist eine Zeichenposition ein Unicode-Offset.  
  
 Zusätzlich zu den von geerbten Methoden `IDebugDocument`, `IDebugDocumentText` Schnittstelle macht die folgenden Methoden verfügbar.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|Gibt die Attribute des Dokuments.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|Gibt die Anzahl der Zeilen und die Anzahl der Zeichen im Dokument zurück.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|Gibt die Position des Zeichens, das erste Zeichen einer Zeile entspricht.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|Gibt die Zeilennummer und optional das Zeichenoffset in der Zeile, die entspricht an der angegebenen Zeichenposition zurück.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|Ruft ab, die Zeichen und/oder die Attribute des Zeichens einem Zeichenposition Bereich zugeordnet.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|Gibt die Zeichenposition Bereich für eine Dokumentenkontext zurück.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|Erstellt ein Dokument Kontextobjekt Bereich der angegebenen Position entspricht.|
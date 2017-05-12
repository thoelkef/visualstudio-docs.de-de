---
title: "IDebugDocumentText-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentText-Schnittstelle"
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentText-Schnittstelle
Bietet Zugriff auf einer nur für Text Debug\- Version des Dokuments.  Diese Schnittstelle verwendet die folgenden Konventionen:  
  
-   Zeichenpositionen und Zeilennummern sind nullbasiert.  
  
-   Zeichenpositionen stellen Zeichenoffsets dar; sie stellen nicht Byte\- oder Wortoffsets dar.  Für Win32 ist eine Zeichenposition ein Unicode\-Offset.  
  
 Zusätzlich zu den von `IDebugDocument` geerbten Methoden macht die `IDebugDocumentText`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|Gibt die Attribute des Dokuments zurück.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|Gibt die Anzahl der Zeilen und die Anzahl der Zeichen im Dokument zurück.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|Gibt Zeichenposition anhand des ersten Zeichens einer Zeile zurück.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|Gibt die Zeilennummer und optional den Zeichenoffset innerhalb der Zeile zurück, die der angegebenen Zeichenposition entspricht.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|Ruft die Zeichen und\/oder die Zeichenattribute ab, die einem Zeichenpositionsbereich zugeordnet werden.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|Gibt den Zeichenpositionsbereich entsprechend einem Dokumentenkontext zurück.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|Erstellt ein Dokumentenkontextobjekt entsprechend dem angegebenen Zeichenpositionsbereich.|
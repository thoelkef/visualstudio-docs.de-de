---
title: "IDebugDocumentPositionOffset2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugDocumentPositionOffset2-Schnittstelle"
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt eine Position in einer Quelldatei als Zeichenoffset dar.  
  
## Syntax  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Wird von der IDE und Module von Debuginformationen genutzt.  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden von `IDebugDocumentPositionOffset2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Ruft den Bereich für die Position des aktuellen Dokuments ab.|  
  
## Hinweise  
 Dies gibt dieselben Informationen wie [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) aber in `char` Offset vom Anfang des Dokuments zurück.  Dadurch wird das Dokument vor, wie es von einem Datenträger. h. ein eindimensionales Array von Zeichen anstelle der Zeilen\- und Spalteninformationen vorhanden wäre, die normalerweise zurückgegeben wurde.  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
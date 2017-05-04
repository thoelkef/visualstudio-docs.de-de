---
title: "IDebugDocumentProvider-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentProvider-Schnittstelle"
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentProvider-Schnittstelle
Stellt eine Möglichkeit für ein Dokument bei Bedarf instanziieren bereit.  
  
## Hinweise  
 Dieses indirekte Möglichkeit zum Instanziieren eines Dokuments:  
  
-   Ermöglicht dem Dokument, um zu laden, wenn es erforderlich ist.  
  
-   Ermöglicht das innerhalb des Debuggers IDE enthalten werden Document\-Objekt.  
  
-   Ermöglicht mehrere Möglichkeiten, auf das gleiche Dokumentobjekt zuzugreifen.  
  
 Dieses effektiv trennt das Dokument von seinem Anbieter und ermöglicht es dem Anbieter, um zusätzliche Laufzeit, Kontextinformationen zu tragen.  
  
 Zusätzlich zu den von `IDebugDocumentInfo` geerbten Methoden macht die `IDebugDocumentProvider`\-Schnittstelle die folgenden Methoden verfügbar.  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Veranlasst das Dokument instanziiert werden, wenn es nicht bereits vorhanden ist.|
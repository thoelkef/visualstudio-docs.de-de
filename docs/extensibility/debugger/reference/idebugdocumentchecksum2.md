---
title: "IDebugDocumentChecksum2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugDocumentChecksum2-Schnittstelle"
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugDocumentChecksum2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt eine Prüfsumme für eine Debug\- Dokument dar und ermöglicht die Übergabe der Prüfsumme zwischen Komponenten.  
  
## Syntax  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle kann von jeder Komponente implementiert werden, die die [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)\-Schnittstelle verfügbar macht.  Allerdings ist es häufig von Debugsymbolinformationen auf Module implementiert, damit die Prüfsumme, die in einer Symboldateien \(\*.pdb\) eingebettet ist in der IDE übergeben und verwendet werden kann, wenn eine Quelle gesucht werden soll.  
  
## Methoden  
 In der folgenden Tabelle werden die Methoden von `IDebugDocumentChecksum2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Ruft den angegebenen prüfsummen\- Dokumenten und Algorithmusbezeichner die maximale Anzahl von Bytes ab.|  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
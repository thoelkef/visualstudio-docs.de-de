---
title: "Language Service-Unterst&#252;tzung f&#252;r das Debuggen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "sprachunterstützung-Debugger"
  - "Language Services, debugging-Unterstützung"
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Language Service-Unterst&#252;tzung f&#252;r das Debuggen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Eine Sprachdienst bieten Funktionen, die einen Debugger über unterstützen die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> Schnittstelle. Zu diesen Funktionen gehören, überprüfen die Haltepunkte und einer Liste mit Ausdrücken, die **Auto** Fenster.  
  
 Sie müssen jedoch eine Auswertung eines Ausdrucks zum Debuggen Ihrer Sprache haben. Die Auswertung eines Ausdrucks ist verantwortlich für das Auswerten von Ausdrücken, um Werte während des Debuggens zu erzeugen. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter:  
  
-   [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Verwalteten Expression Evaluator\-Beispiel](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## Kompilierungsausgabe  
 Der Typ des Compilers bestimmt, was Sie tun, um das Debuggen für Ihre Sprache zu implementieren. Wenn der Compiler das Windows\-Betriebssystem betrifft und eine PDB\-Datei schreibt, können Sie Programme debuggen, mit dem systemeigenen Code Debugmodul, die in Visual Studio integriert ist. Wenn der Compiler Microsoft intermediate Language \(MSIL\) erzeugt, können Sie Programme debuggen, mit der verwaltete Code Debugmodul, das auch in Visual Studio integriert ist. Wenn der Compiler einen proprietären Betriebssystem oder einer anderen Common Language Runtime\-Umgebung ausgerichtet ist, müssen Sie Ihre eigenen Debugmodul schreiben.  
  
 Weitere Informationen zum Debuggen für Ihre Sprache implementieren, finden Sie unter [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) in Visual Studio Debugging\-SDK.
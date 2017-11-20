---
title: "Language Service unterstützt das Debuggen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb57f7efa13a31ee4c68340936955624189e285d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="language-service-support-for-debugging"></a>Language Service unterstützt das Debuggen
Geben Sie ein Sprachdienst kann Funktionen, die einen Debugger über unterstützen die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> Schnittstelle. Zu diesen Funktionen gehören Haltepunkte überprüfen und die Angabe einer Liste mit Ausdrücken, die die **"Auto"** Fenster.  
  
 Allerdings müssen Sie eine ausdrucksauswertung So debuggen Sie Ihre Sprache haben. Die ausdrucksauswertung ist verantwortlich für das Auswerten von Ausdrücken, um Werte während des Debuggens zu erzeugen. Informationen zu CLR-ausdrucksauswertungen implementieren finden Sie unter:  
  
-   [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Verwaltete Ausdrucksauswertung (Beispiel)](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Kompilierungsausgabe  
 Der Typ des Compilers bestimmt, was Sie tun, um das Debuggen für Ihre Sprache implementieren müssen. Wenn der Compiler das Betriebssystem Windows betrifft und eine PDB-Datei schreibt, können Sie Programme debuggen, mit dem systemeigenen Code Debugmodul, die in Visual Studio integriert ist. Wenn der Compiler Microsoft intermediate Language (MSIL) erzeugt, können Sie Programme debuggen, durch den verwalteten Code Debugmodul, das auch in Visual Studio integriert ist. Wenn der Compiler eine proprietäre Betriebssystem oder einer anderen Laufzeitumgebung ausgerichtet ist, müssen Sie eigene Debugmodul zu schreiben.  
  
 Weitere Informationen zum Debuggen für Ihre Sprache implementieren, finden Sie unter [Einstieg](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) in Visual Studio Debugging-SDK.
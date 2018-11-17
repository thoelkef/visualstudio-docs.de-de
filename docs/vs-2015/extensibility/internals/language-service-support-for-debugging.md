---
title: Sprachdienstunterstützung für das Debuggen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7141c7a6b3845edda6888e1ed33abfbf8af37988
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51809687"
---
# <a name="language-service-support-for-debugging"></a>Sprachdienstunterstützung für das Debuggen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Sprachdienst bieten Funktionen, die einen Debugger über unterstützen die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> Schnittstelle. Zu diesen Funktionen gehören, Überprüfen von Haltepunkten und die Angabe einer Liste mit Ausdrücken, die die **"Auto"** Fenster.  
  
 Allerdings benötigen Sie eine ausdrucksauswertung, um Ihre Sprache zu debuggen. Die ausdrucksauswertung ist verantwortlich für das Auswerten von Ausdrücken, um Werte während des Debuggens zu erzeugen. Informationen zum Implementieren von CLR-ausdrucksauswertungen finden Sie unter:  
  
-   [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
-   [Beispiele für verwaltete Ausdrucksauswertung](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Kompilierungsausgabe  
 Der Typ der Compiler bestimmt, was Sie tun, um das Debuggen für Ihre Sprache zu implementieren. Wenn Ihre Compiler das Windows-Betriebssystem betrifft und eine PDB-Datei schreibt, können Sie Programme debuggen, mit dem systemeigenen Code Debuggen-Engine, die in Visual Studio integriert ist. Wenn Ihr Compiler Microsoft intermediate Language (MSIL) erzeugt, können Sie Programme debuggen, mit den verwalteten Code Debuggen-Engine, die auch in Visual Studio integriert ist. Wenn der Compiler ein proprietäres Operating System oder eine andere Runtime-Umgebung ausgerichtet ist, müssen Sie Ihre eigenen Debug-Engine zu schreiben.  
  
 Weitere Informationen zum Implementieren von Debuggen, die für Ihre Sprache finden Sie unter [Einstieg](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) in Visual Studio Debugging SDK.


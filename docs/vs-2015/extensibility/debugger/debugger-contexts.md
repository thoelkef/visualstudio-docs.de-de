---
title: Debugger-Kontexte | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 771a3cd8ae25173f3033b3a3229e516570f5dedc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200634"
---
# <a name="debugger-contexts"></a>Debuggerkontexte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Beim [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debuggen arbeitet die Debug-Engine (de) in mehreren unterschiedlichen Kontexten gleichzeitig wie folgt:  
  
- Der Code Kontext, der die aktuelle Position im ausführungsstream eines Programms beschreibt.  
  
- Der Dokumentations Kontext oder die Position, in der die aktuelle Position in einem Quelldokument beschrieben wird.  
  
- Der Ausdrucks Auswertungs Kontext, der den Kontext beschreibt, in dem die Ausdrucks Auswertung stattfindet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Codekontext](../../extensibility/debugger/code-context.md)  
 Erläutert den Code Kontext als Adresse im Anweisungs Datenstrom eines Programms in den heutigen Lauf Zeit Architekturen im Vergleich zu nicht herkömmlichen Sprachen, in denen Code möglicherweise nicht durch Anweisungen dargestellt wird, aber auf andere Weise.  
  
 [Dokumentposition](../../extensibility/debugger/document-position.md)  
 Definiert die Dokument Position im Visual Studio-Debuggen durch eine Abstraktion einer Position in einer Quelldatei, die der IDE bekannt ist.  
  
 [Dokumentkontext](../../extensibility/debugger/document-context.md)  
 Erläutert, was Dokument Kontext in Visual Studio-Debuggen in Bezug auf eine Quelldatei darstellt. Erläutert auch, wie der Symbol Handler einem Dokumentations Kontext einen Code Kontext zuordnet.  
  
 [Ausdrucksauswertungskontext](../../extensibility/debugger/expression-evaluation-context.md)  
 Stellt Informationen zu einem Ausdrucks Auswertungs Kontext in Visual Studio bereit. Ein Ausdrucks Auswertungs Kontext, der einem Stapel Rahmen zugeordnet ist, stellt z. b. den Kontext zum Auswerten von lokalen Variablen, Methoden Parametern und Klassenmembern bereit.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debugkonzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte der debuggingarchitektur.  
  
 [Debugging von Komponenten](../../extensibility/debugger/debugger-components.md)  
 Bietet eine Übersicht über die Visual Studio-debuggingkomponenten, die Debug-Engine (de), Ausdrucks Auswertung (EE) und Symbol Handler (SH) enthalten.  
  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu verschiedenen Debuggingaufgaben, z. b. das Starten eines Programms und Auswerten von Ausdrücken.

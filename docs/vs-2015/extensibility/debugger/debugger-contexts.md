---
title: Debuggerkontexte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7f24360b29557ef767d1a9a5f91a6f116db9ec12
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523011"
---
# <a name="debugger-contexts"></a>Debuggerkontexte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Debugger Kontexten](https://docs.microsoft.com/visualstudio/extensibility/debugger/debugger-contexts).  
  
In [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debuggen, die Debug-Engine (DE) arbeitet gleichzeitig in mehreren unterschiedlichen Kontexten wie folgt:  
  
-   Der Codekontext, der die aktuelle Position in der Ausführung eines Programms-Stream beschreibt.  
  
-   Die Dokumentation Kontext oder die Position, die die aktuelle Position in einem Quelldokument beschreibt.  
  
-   Der Ausdruck Evaluation-Kontext, der den Kontext beschreibt, in dem den Ausdruck Auswertung stattfinden soll.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Codekontext](../../extensibility/debugger/code-context.md)  
 Erläutert Codekontext als eine Adresse im Anweisungsstream eines Programms, in heutigen Laufzeit-Architekturen im Vergleich zu nicht traditionelle Sprachen, in dem Code nicht von Anweisungen, aber auf andere Weise dargestellt werden können.  
  
 [Dokumentposition](../../extensibility/debugger/document-position.md)  
 Definiert die Dokumentposition in Visual Studio-debugging über eine Abstraktion einer Position in einer Quelldatei an, wie die IDE bekannt.  
  
 [Dokumentkontext](../../extensibility/debugger/document-context.md)  
 Erläutert, welche Dokumentenkontext darstellt, in Visual Studio-debugging in Bezug auf eine Quelldatei. Außerdem wird erläutert, wie der Symbol-Handler einen Codekontext Dokumentation Kontext zugeordnet.  
  
 [Ausdrucksauswertungskontext](../../extensibility/debugger/expression-evaluation-context.md)  
 Enthält Informationen über eine ausdrucksauswertungskontext in Visual Studio. Beispielsweise liefert eine ausdrucksauswertungskontext einen Stapelrahmen zugeordnet den Kontext für Ihre Evaluierung von lokalen Variablen, Methodenparameter und Klassenmember.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggingkonzepte kennen](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte für das Debuggen Architektur an.  
  
 [Debuggen von Komponenten](../../extensibility/debugger/debugger-components.md)  
 Bietet eine Übersicht über die Visual Studio-debugging-Komponenten an, die die Debug-Engine (DE), die ausdrucksauswertung (EE) und die Symbol-Handler (SH) enthalten.  
  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu verschiedenen Debuggen Aufgaben wie das Starten eines Programms und Auswerten von Ausdrücken.


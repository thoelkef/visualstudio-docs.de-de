---
title: Debugger-Kontexten | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f36df39cf29ff298a327ec6e6d4bb02ff53485a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-contexts"></a>Debugger-Kontexte
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen, Debugging-Modul (DE) arbeitet gleichzeitig in mehreren unterschiedlichen Kontexten wie folgt:  
  
-   Der Codekontext, der die aktuelle Position im Datenstrom der Ausführung eines Programms beschrieben wird.  
  
-   Die Dokumentation Kontext oder die Position, die die aktuelle Position in einem Quelldokument beschreibt.  
  
-   Der Ausdruck Evaluation-Kontext, der den Kontext beschreibt, in dem den Ausdruck Auswertung stattfindet.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Codekontext](../../extensibility/debugger/code-context.md)  
 Erläutert Codekontext als Adresse in einem Programm Anweisungsstream in heutigen zur Laufzeit Architekturen im Vergleich zu traditionelle Sprachen, in dem Code nicht von Anweisungen, aber auch auf andere Weise dargestellt werden kann.  
  
 [Dokumentposition](../../extensibility/debugger/document-position.md)  
 Definiert die Dokumentposition in Visual Studio debuggen, über eine Abstraktion einer Position in einer Quelldatei, da die IDE bekannt.  
  
 [Dokumentkontext](../../extensibility/debugger/document-context.md)  
 Erläutert, welche Dokument in Visual Studio debuggen, im Verhältnis zu einer Quelldatei darstellt. Außerdem erläutert, wie der Symbol-Handler einen Codekontext Dokumentation Kontext zugeordnet.  
  
 [Ausdrucksauswertungskontext](../../extensibility/debugger/expression-evaluation-context.md)  
 Enthält Informationen zu einem Evaluierungskontext Ausdruck in Visual Studio. Ein Ausdruck Evaluierungskontext einen Stapelrahmen zugeordnet bietet z. B. den Kontext für die Bewertung von lokalen Variablen, Methodenparameter und Klassenmember an.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggen-Konzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte für das Debuggen Architektur.  
  
 [Debuggen von Komponenten](../../extensibility/debugger/debugger-components.md)  
 Bietet eine Übersicht über Visual Studio debugging-Komponenten, z. B. die Debugging-Modul (DE), ausdrucksauswertung (EE) und Symbol Handler ("SH").  
  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)  
 Enthält Links zu verschiedenen Debugaufgaben, z. B. ein Programm starten und Auswerten von Ausdrücken.
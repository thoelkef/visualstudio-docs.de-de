---
title: Erweiterbarkeit von Visual Studio-Debugger | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b8d37954bf238b2ed1323bf021fded94ec0c584
ms.sourcegitcommit: 3a19319e2599bd193fb2ca32020ca53942974bfd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983666"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio Debugger-Erweiterbarkeit
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio enthält einen vollständig interaktiven Quellcode-Debugger, der ein leistungsfähiges und einfach zu verwendende Tool zum Nachverfolgen von Fehlern in Ihrem Programm bereitstellt. Der Debugger verfügt über eine umfassende unter C#Stützung Visual Basic,C++, C/und JavaScript. Mit dem [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], das im [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=21835)verfügbar ist, können jedoch andere Programmiersprachen im Debugger mit denselben umfangreichen Features unterstützt werden.  
  
 Der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugger ist das allgemeine Front-End (d. h. die Benutzeroberfläche) für die debuggingkomponenten, die wiederum spezifisch für die zu debuggende Sprache sind. Bei neuen Sprachen ist für die Unterstützung durch den [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugger lediglich die Erstellung der erforderlichen Back-End-Komponenten, z. b. Debug-Engine (de), erforderlich. An dieser Stelle kommt der [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] ins Spiel.  
  
 Die [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] enthält einen vollständigen Verweis auf alle [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Elemente, die zum Erstellen einer neuen de erforderlich sind. Außerdem finden Sie Beispiele und Lernprogramme, die Ihnen beim Einstieg helfen.  
  
 Ein End-to-End-Beispiel für ein Sprachprojekt System mit Debugunterstützung finden Sie im [IronPython-Beispiel](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 In den folgenden Abschnitten wird beschrieben, wie der Debugger mithilfe der [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]erweitert wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Beschreibt, was [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debugging bietet und wie das SDK installiert wird.  
  
 [Erstellen einer benutzerdefinierten Debug-Engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Dokumentiert den benutzerdefinierten de-Prozess, von der Vorbereitung des Programms bis zum Trennen der de.  
  
 [Schreiben einer CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Erläutert, ob Sie eine Ausdrucks Auswertung schreiben müssen.  
  
 [Auswählen einer Implementierungsstrategie für die Debug-Engine](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Erläutert, wie Sie Ihre de implementieren.  
  
 [Verweis](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Dokumentiert die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debug-API.  
  
 [Proben](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Enthält Links zu einem Beispiel für Common Language Runtime Ausdrucks Auswertung und eine Debug-Engine.

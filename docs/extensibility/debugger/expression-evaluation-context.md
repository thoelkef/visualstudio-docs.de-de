---
title: Ausdruck Evaluierungskontext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d1fade5bb18e59a1b9b9e2655ce01b0b5559484e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099144"
---
# <a name="expression-evaluation-context"></a>Evaluierungskontext Ausdruck
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen, ein **Ausdruck Evaluierungskontext**:  
  
-   Stellt einen Kontext für die Auswertung von Ausdrücken. Im Allgemeinen entspricht ein Evaluierungskontext die lexikalischen Gültigkeitsbereich in dem Variablen, Parameter, Funktionen und Methoden ausgewertet werden soll. Beispielsweise wird ein Ausdruck Evaluierungskontext einen Stapelrahmen zugeordnet der Kontext bereitstellt, für die Bewertung von lokalen Variablen, Methodenparameter und Klassenmember (falls zutreffend).  
  
-   Liegt vor, wenn ein Programm an einem Haltepunkt angehalten wurde. Der Ausdruck selbst ist eine Datenstruktur, die einen analysierten Ausdruck, der für die Bindung und der Auswertung innerhalb des angegebenen Kontexts kann darstellt.  
  
     Im Detail, werden Ausdrücke erstellt, mit der [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Methode. Wenn ein Ausdruck ausgewertet wird, wird eine druckbare Zeichenfolge, die mit dem Namen und Typ der Variable "oder" Argument "und" den Wert generiert. Diese Zeichenfolge wird im Überwachungsfenster oder im Fenster "lokal" von der IDE angezeigt.  
  
     Erhält eine `BSTR` und ein [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle, ein Debugging-Modul (DE) kann erstellen eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Schnittstelle durch Analysieren eines Ausdrucks. Erhält eine `IDebugExpression2` -Schnittstelle, die DE kann durch synchrone oder asynchrone ausdrucksauswertung einen Wert abrufen. Dieser Wert zusammen mit dem Namen und Typ der Variable oder eines Arguments, wird für die Anzeige der IDE gesendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdruck Auswertung Schnittstellen](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)
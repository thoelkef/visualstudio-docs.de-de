---
title: Ausdrucksauswertungskontext | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 15b7f53dddefa78ef58818d20b5ca6eafb84e207
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835736"
---
# <a name="expression-evaluation-context"></a>Ausdrucksauswertungskontext
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen, ein **ausdrucksauswertungskontext**:  
  
-   Stellt einen Kontext für ausdrucksauswertung dar. Im Allgemeinen entspricht ein Evaluierungskontext den lexikalischen Gültigkeitsbereich in der Variablen, Parameter, Funktionen und Methoden zu bewerten. Beispielsweise wird ein ausdrucksauswertungskontext einen Stapelrahmen zugeordnet Kontext bereitstellen, für Ihre Evaluierung von lokalen Variablen, Methodenparameter und Klassenmember (falls zutreffend).  
  
-   Ist vorhanden, wenn ein Programm an einem Haltepunkt beendet wurde. Der Ausdruck selbst ist eine Datenstruktur, die einen analysierten Ausdruck, der bereit für die Bindung und Auswerten von innerhalb des angegebenen Kontexts darstellt.  
  
     Im Detail, werden Ausdrücke erstellt, mit der [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Methode. Wenn ein Ausdruck ausgewertet wird, generiert er eine druckbare Zeichenfolge, die den Namen und Typ der Variablen "oder" Argument "und" den Wert enthält. Diese Zeichenfolge wird in das Überwachungsfenster oder im Fenster "lokal" der IDE angezeigt.  
  
     Erhält eine `BSTR` und [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle, die eine Debug-Engine (DE) erstellen kann eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle durch die Analyse eines Ausdrucks. Erhält ein `IDebugExpression2` -Schnittstelle, die DE kann durch synchrone oder asynchrone ausdrucksauswertung einen Wert abrufen. Dieser Wert zusammen mit dem Namen und Typ der Variablen oder des Arguments, wird für die Anzeige der IDE gesendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Schnittstellen für die ausdrucksauswertung](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)
---
title: Ausdrucksbewertungskontext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e939a4fa5f4673e2f701206c96599c54bc0c3b51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738737"
---
# <a name="expression-evaluation-context"></a>Ausdrucksbewertungskontext
Beim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen ein **Ausdrucksauswertungskontext:**

- Stellt einen Kontext für die Ausdrucksauswertung dar. Im Allgemeinen entspricht ein Auswertungskontext dem lexikalischen Bereich, innerhalb dessen Variablen, Parameter, Funktionen und Methoden ausgewertet werden können. Beispielsweise stellt ein Ausdrucksauswertungskontext, der einem Stapelrahmen zugeordnet ist, den Kontext zum Auswerten lokaler Variablen, Methodenparameter und Klassenmember (falls zutreffend) bereit.

- Ist vorhanden, wenn ein Programm an einem Haltepunkt angehalten wurde. Der Ausdruck selbst ist eine Datenstruktur, die einen analysierten Ausdruck darstellt, der für die Bindung und Auswertung innerhalb des angegebenen Kontexts bereit ist.

     Im Detail werden Ausdrücke mit der [ParseText-Methode](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) erstellt. Wenn ein Ausdruck ausgewertet wird, generiert er eine druckbare Zeichenfolge, die den Namen und Typ der Variablen oder des Arguments und ihren Wert enthält. Diese Zeichenfolge wird im Überwachungsfenster oder im Locals-Fenster der IDE angezeigt.

     Bei `BSTR` einer und einer [IDebugExpressionContext2-Schnittstelle](../../extensibility/debugger/reference/idebugexpressioncontext2.md) kann ein Debugmodul (DE) eine [IDebugExpression2-Schnittstelle](../../extensibility/debugger/reference/idebugexpression2.md) erstellen, indem es einen Ausdruck analysiert. Bei `IDebugExpression2` einer Schnittstelle kann die DE einen Wert durch synchrone oder asynchrone Ausdrucksauswertung abrufen. Dieser Wert wird zusammen mit dem Namen und Typ der Variablen oder des Arguments zur Anzeige an die IDE gesendet.

## <a name="see-also"></a>Weitere Informationen
- [Ausdrucksauswertungsschnittstellen](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)

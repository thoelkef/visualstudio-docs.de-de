---
title: Ausdrucks Auswertungs Kontext | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738737"
---
# <a name="expression-evaluation-context"></a>Ausdrucks Auswertungs Kontext
Beim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen ein **Ausdrucks Auswertungs Kontext**:

- Stellt einen Kontext für die Ausdrucks Auswertung dar. Im Allgemeinen entspricht ein Evaluierungs Kontext dem lexikalischen Gültigkeitsbereich, in dem Variablen, Parameter, Funktionen und Methoden ausgewertet werden. Ein Ausdrucks Auswertungs Kontext, der einem Stapel Rahmen zugeordnet ist, stellt z. b. den Kontext zum Auswerten lokaler Variablen, Methoden Parameter und Klassenmember bereit (falls zutreffend).

- Ist vorhanden, wenn ein Programm an einem Haltepunkt angehalten wurde. Der Ausdruck selbst ist eine Datenstruktur, die einen analysierten Ausdruck darstellt, der zum Binden und auswerten innerhalb des angegebenen Kontexts bereit ist.

     Im Detail werden Ausdrücke mithilfe der Methode " [Parser Text](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) " erstellt. Wenn ein Ausdruck ausgewertet wird, generiert er eine druckbare Zeichenfolge, die den Namen und Typ der Variablen oder des Arguments und seinen Werts enthält. Diese Zeichenfolge wird im Überwachungsfenster oder im Fenster Lokal der IDE angezeigt.

     Wenn eine `BSTR` und eine [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) -Schnittstelle angegeben sind, kann eine Debug-Engine (de) eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) -Schnittstelle erstellen, indem Sie einen Ausdruck initialisieren. Bei einer `IDebugExpression2` Schnittstelle kann der Wert durch synchrone oder asynchrone Ausdrucks Auswertung einen Wert erhalten. Dieser Wert wird zusammen mit dem Namen und dem Typ der Variablen oder des Arguments zur Anzeige an die IDE gesendet.

## <a name="see-also"></a>Weitere Informationen
- [Ausdrucks Bewertungs Schnittstellen](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Debugger-Kontexte](../../extensibility/debugger/debugger-contexts.md)

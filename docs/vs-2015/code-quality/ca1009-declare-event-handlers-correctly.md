---
title: 'CA1009: Ereignishandler korrekt deklarieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6a4a4e2e6990772b50568043c4d18ff29248571d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547887"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Ereignishandler korrekt deklarieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Delegat, der ein öffentliches oder geschütztes Ereignis behandelt, weist nicht die richtige Signatur, den Rückgabetyp oder die richtigen Parameternamen auf.

## <a name="rule-description"></a>Beschreibung der Regel
 Ereignishandlermethoden nehmen zwei Parameter an. Der erste ist vom Typ <xref:System.Object?displayProperty=fullName> und hat den Namen "Sender". Dies ist das Objekt, durch das das Ereignis ausgelöst wurde. Der zweite Parameter ist vom Datentyp und hat den <xref:System.EventArgs?displayProperty=fullName> Namen "e". Dies sind die Daten, die dem Ereignis zugeordnet sind. Wenn das Ereignis beispielsweise ausgelöst wird, wenn eine Datei geöffnet wird, enthalten die Ereignisdaten in der Regel den Namen der Datei.

 Ereignishandlermethoden sollten keinen Wert zurückgeben. In der Programmiersprache c# wird dies durch den Rückgabetyp angegeben `void` . Ein Ereignishandler kann mehrere Methoden in mehreren Objekten aufrufen. Wenn die Methoden einen Wert zurückgeben können, werden mehrere Rückgabewerte für jedes Ereignis auftreten, und nur der Wert der letzten aufgerufenen Methode wäre verfügbar.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Signatur, den Rückgabetyp oder die Parameternamen des Delegaten. Weitere Informationen finden Sie im folgenden Beispiel.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Delegaten, der für die Behandlung von Ereignissen geeignet ist. Die Methoden, die von diesem Ereignishandler aufgerufen werden können, entsprechen der Signatur, die in den Entwurfs Richtlinien angegeben ist. `AlarmEventHandler`der Typname des Delegaten. `AlarmEventArgs`wird von der-Basisklasse für Ereignisdaten abgeleitet <xref:System.EventArgs> und enthält Alarmereignis Daten.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2109: Sichtbare Ereignishandler überprüfen.](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Weitere Informationen
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [NIB: Ereignisse und Delegaten](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)

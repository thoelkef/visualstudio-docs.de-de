---
title: 'DA0012: Starke Reflektion | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6257ce96e139e173fca804221b495f7467fc6b20
ms.sourcegitcommit: bb5425b9c6d8fd7135d9584c2963831754071347
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "73024650"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Starke Reflektion

|||
|-|-|
|Regel-ID|DA0012|
|Kategorie|.NET Framework-Verwendung|
|Profilerstellungsmethoden|Sampling|
|Meldung|Möglicherweise verwenden Sie Reflektion zu häufig. Dieser Vorgang ist äußerst speicherintensiv.|
|Regeltyp|Warnung|

## <a name="cause"></a>Ursache
 Aufrufe der System.Reflection-Methoden (beispielsweise „InvokeMember“ oder „GetMember“) oder der Type-Methoden (beispielsweise „MemberInvoke“) machen einen großen Teil der Profilerstellungsdaten aus. Ersetzen Sie diese Methoden nach Möglichkeit durch eine frühe Bindung an Methoden abhängiger Assemblys.

## <a name="rule-description"></a>Regelbeschreibung
 Reflektion ist eine flexible Funktion von .NET Framework, die verwendet werden kann, um eine späte Bindung der Anwendung an eine abhängige Laufzeitassembly auszuführen oder neue Typen während der Laufzeit zu erstellen und dynamisch auszuführen. Diese Verfahren können jedoch die Leistung beeinträchtigen, wenn sie häufig verwendet oder in engen Schleifen aufgerufen werden.

 Weitere Informationen finden Sie im Abschnitt [Reflection and Late Binding (Reflektion und späte Bindung)](/previous-versions/msp-n-p/ff647790(v=pandp.10)#reflection-and-late-binding) in „Chapter 5 – Improving Managed Code Performance (Kapitel 5 – Verbessern der Leistung von verwaltetem Code)“ im Band „Improving .NET Application Performance and Scalability (Verbessern von Leistung und Skalierbarkeit von .NET-Anwendungen)“ der Microsoft-Bibliothek für „Muster und Vorgehensweisen“ im MSDN.

## <a name="how-to-investigate-a-warning"></a>Vorgehensweise zur Überprüfung einer Warnung
 Doppelklicken Sie auf die Meldung im Fenster „Fehlerliste“, um zur [Funktionsdetailansicht](../profiling/function-details-view.md) der Profilerstellungsdaten zu navigieren. Suchen Sie in den aufrufenden Funktionen der System.Type-Methode oder der System.Reflection-Methode nach Programmabschnitten, von denen die .NET-Reflektions-APIs am häufigsten verwendet werden. Vermeiden Sie die Verwendung von Methoden, von denen Metadaten zurückgegeben werden. Wenn es auf die Leistung der Anwendung ankommt, sollten Sie möglichst keine späte Bindung verwenden und Typen nicht zur Laufzeit dynamisch erstellen.
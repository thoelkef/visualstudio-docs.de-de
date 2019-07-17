---
title: 'DA0012: Starke Reflektion | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ae0f361d4bbfe48b3133e50c360f66387d555814
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187863"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Starke Reflektion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-Id | DA0012 |  
| Kategorie |. NET Framework-Verwendung |  
| Profilerstellungsmethoden | Erstellen von Stichproben |  
| Nachricht | Sie können Reflektion übermäßig verwendet werden. Dieser Vorgang ist äußerst speicherintensiv.|  
| Regeltyp | Warnung |  
  
## <a name="cause"></a>Ursache  
 Aufrufe der System.Reflection-Methoden (beispielsweise „InvokeMember“ oder „GetMember“) oder der Type-Methoden (beispielsweise „MemberInvoke“) machen einen großen Teil der Profilerstellungsdaten aus. Ersetzen Sie diese Methoden nach Möglichkeit durch eine frühe Bindung an Methoden abhängiger Assemblys.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Reflektion ist eine flexible Funktion von .NET Framework, die verwendet werden kann, um eine späte Bindung der Anwendung an eine abhängige Laufzeitassembly auszuführen oder neue Typen während der Laufzeit zu erstellen und dynamisch auszuführen. Diese Verfahren können jedoch die Leistung beeinträchtigen, wenn sie häufig verwendet oder in engen Schleifen aufgerufen werden.  
  
 Weitere Informationen finden Sie im Abschnitt [Reflection and Late Binding (Reflektion und späte Bindung)](http://go.microsoft.com/fwlink/?LinkId=177826) in „Chapter 5 – Improving Managed Code Performance (Kapitel 5 – Verbessern der Leistung von verwaltetem Code)“ im Band „Improving .NET Application Performance and Scalability (Verbessern von Leistung und Skalierbarkeit von .NET-Anwendungen)“ der Microsoft-Bibliothek für „Muster und Vorgehensweisen“ im MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Vorgehensweise bei der Überprüfung einer Warnung  
 Doppelklicken Sie auf die Meldung im Fenster „Fehlerliste“, um zur [Funktionsdetailansicht](../profiling/function-details-view.md) der Profilerstellungsdaten zu navigieren. Suchen Sie in den aufrufenden Funktionen der System.Type-Methode oder der System.Reflection-Methode nach Programmabschnitten, von denen die .NET-Reflektions-APIs am häufigsten verwendet werden. Vermeiden Sie die Verwendung von Methoden, von denen Metadaten zurückgegeben werden. Wenn es auf die Leistung der Anwendung ankommt, sollten Sie möglichst keine späte Bindung verwenden und Typen nicht zur Laufzeit dynamisch erstellen.

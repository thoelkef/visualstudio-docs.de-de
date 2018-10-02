---
title: 'DA0012: Starke Reflektion | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 458f1bc74d8660e640139bff2f379a66eafa2919
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512917"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Starke Reflektion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [DA0012: viel Reflektion](https://docs.microsoft.com/visualstudio/profiling/da0012-significant-amount-of-reflection).  
  
Regel-Id | DA0012 |  
| Kategorie |. NET Framework-Verwendung |  
| Profilerstellungsmethoden | Erstellen von Stichproben |  
| Nachricht | Sie können Reflektion übermäßig verwendet werden. Es ist ein kostenintensiver Vorgang. |  
| Regeltyp | Warnung |  
  
## <a name="cause"></a>Ursache  
 Aufrufe der System.Reflection-Methoden (beispielsweise „InvokeMember“ oder „GetMember“) oder der Type-Methoden (beispielsweise „MemberInvoke“) machen einen großen Teil der Profilerstellungsdaten aus. Ersetzen Sie diese Methoden nach Möglichkeit durch eine frühe Bindung an Methoden abhängiger Assemblys.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Reflektion ist eine flexible Funktion von .NET Framework, die verwendet werden kann, um eine späte Bindung der Anwendung an eine abhängige Laufzeitassembly auszuführen oder neue Typen während der Laufzeit zu erstellen und dynamisch auszuführen. Diese Verfahren können jedoch die Leistung beeinträchtigen, wenn sie häufig verwendet oder in engen Schleifen aufgerufen werden.  
  
 Weitere Informationen finden Sie im Abschnitt [Reflection and Late Binding (Reflektion und späte Bindung)](http://go.microsoft.com/fwlink/?LinkId=177826) in „Chapter 5 – Improving Managed Code Performance (Kapitel 5 – Verbessern der Leistung von verwaltetem Code)“ im Band „Improving .NET Application Performance and Scalability (Verbessern von Leistung und Skalierbarkeit von .NET-Anwendungen)“ der Microsoft-Bibliothek für „Muster und Vorgehensweisen“ im MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Vorgehensweise bei der Überprüfung einer Warnung  
 Doppelklicken Sie auf die Meldung im Fenster „Fehlerliste“, um zur [Funktionsdetailansicht](../profiling/function-details-view.md) der Profilerstellungsdaten zu navigieren. Suchen Sie in den aufrufenden Funktionen der System.Type-Methode oder der System.Reflection-Methode nach Programmabschnitten, von denen die .NET-Reflektions-APIs am häufigsten verwendet werden. Vermeiden Sie die Verwendung von Methoden, von denen Metadaten zurückgegeben werden. Wenn es auf die Leistung der Anwendung ankommt, sollten Sie möglichst keine späte Bindung verwenden und Typen nicht zur Laufzeit dynamisch erstellen.




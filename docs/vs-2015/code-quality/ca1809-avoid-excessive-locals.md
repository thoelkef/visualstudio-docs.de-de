---
title: 'CA1809: übermäßige lokale Variablen vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d23d9cc6006997c82451ac061e3ee0353e59b1b9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671494"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Übermäßige lokale Variablen vermeiden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Kategorie|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Member enthält mehr als 64 lokale Variablen, von denen einige möglicherweise vom Compiler generiert werden.

## <a name="rule-description"></a>Regelbeschreibung
 Eine häufige Leistungsoptimierung besteht darin, einen Wert in einem Prozessor Register anstelle von im Arbeitsspeicher zu speichern. Dies wird als *registrieren* des Werts bezeichnet. Der Common Language Runtime berücksichtigt bis zu 64 lokale Variablen für die Registrierung. Variablen, die nicht registriert werden, werden auf dem Stapel abgelegt und müssen vor der Bearbeitung in ein Register verschoben werden. Um die Wahrscheinlichkeit zuzulassen, dass alle lokalen Variablen registriert werden, begrenzen Sie die Anzahl der lokalen Variablen auf 64.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen Sie die Implementierung so umgestalten, dass nicht mehr als 64 lokale Variablen verwendet werden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken oder die Regel zu deaktivieren, wenn die Leistung kein Problem ist.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)

---
title: 'CA1809: Übermäßige lokale Variablen vermeiden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c41836e2a7e7e5530d83ff0eaf854b88de42f38f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589741"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Übermäßige lokale Variablen vermeiden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA1809: übermäßige lokale Variablen vermeiden](https://docs.microsoft.com/visualstudio/code-quality/ca1809-avoid-excessive-locals).

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Element enthält mehr als 64 lokale Variablen, von die einige Compiler generiert werden kann.

## <a name="rule-description"></a>Regelbeschreibung
 Zur Optimierung der allgemeinen Leistung ist zum Speichern eines Werts in einem Prozessorregister statt im Speicher, der als bezeichnet wird *Ablaufanalyse* den Wert. Die common Language Runtime betrachtet, bis zu 64 lokale Variablen für die Registrierung in Betracht. Variablen, die nicht registriert werden, die auf dem Stapel abgelegt werden und müssen vor der Bearbeitung in ein Register verschoben werden. Um die Möglichkeit, dass alle lokale Variablen registriert werden, die Anzahl der lokalen Variablen auf 64 beschränken.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Umgestalten Sie, um einen Verstoß gegen diese Regel zu beheben, die Implementierung, um nicht mehr als 64 lokale Variablen verwenden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, um eine Warnung dieser Regel zu unterdrücken, oder um die Regel zu deaktivieren, wenn die Leistung kein Problem darstellt.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)




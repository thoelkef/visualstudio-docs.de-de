---
title: 'CA1505: nicht wart baren Code vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 87aacfd675181e35d289b2a054c58f83f3f790fa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607590"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Nicht wartbaren Code vermeiden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Vermeidunmantainablecode|
|CheckId|CA1505|
|Kategorie|Microsoft. Wartbarkeit|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ oder eine Methode verfügt über einen niedrigen Wartbarkeitsindexwert.

## <a name="rule-description"></a>Regelbeschreibung
 Der Wartbarkeitsindex wird mithilfe der folgenden Metriken berechnet: Codezeilen, Programm Volume und zyklomatische Komplexität. Das Programm Volume ist ein Maß für die Schwierigkeit, ein Typ oder eine Methode zu verstehen, die auf der Anzahl von Operatoren und Operanden im Code basiert. Die zyklomatische Komplexität ist ein Maß für die strukturelle Komplexität des Typs oder der Methode. Weitere Informationen zu Codemetriken finden Sie unter [Messen der Komplexität und Verwaltbarkeit von verwaltetem Code](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

 Ein niedriger Wartbarkeitsindex gibt an, dass ein Typ oder eine Methode wahrscheinlich schwierig zu verwalten ist, und wäre ein guter Kandidat für die Umgestaltung.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entwerfen Sie zum Beheben dieses Verstoßes den Typ oder die Methode neu, und versuchen Sie, ihn in kleinere und stärker fokussierte Typen oder Methoden aufzuteilen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Schließen Sie diese Warnung aus, wenn ein Typ oder eine Methode trotz ihrer großen Größe weiterhin als wart Bar eingestuft wird oder wenn der Typ oder die Methode nicht aufgeteilt werden kann.

## <a name="see-also"></a>Siehe auch
 [Wart barkeits Warnungen](../code-quality/maintainability-warnings.md) , die die [Komplexität und Verwaltbarkeit von verwaltetem Code Messen](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)

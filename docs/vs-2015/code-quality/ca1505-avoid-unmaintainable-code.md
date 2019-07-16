---
title: 'CA1505: Nicht wartbaren Code vermeiden | Microsoft-Dokumentation'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d9d5dc976c27ca2459fa64b95fe0502579a500b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191213"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Nicht wartbaren Code vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUnmantainableCode|
|CheckId|CA1505|
|Kategorie|Microsoft.Maintainability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Typ oder eine Methode verfügt über einen niedrigen Wartbarkeitsindexwert.

## <a name="rule-description"></a>Regelbeschreibung
 Der Wartbarkeitsindex wird berechnet, indem Sie die folgenden Metriken: Zeilen Code, Programm-Volume und zyklomatische Komplexität. Programm-Volume ist ein Maß für die Schwierigkeit der Überblick über einen Typ oder Methode, die basierend auf der Anzahl von Operatoren und Operanden in den Code. Zyklomatische Komplexität ist ein Maß der strukturellen Komplexität des Typs oder -Methode. Weitere Informationen finden Sie Informationen zu codemetriken auf [Messen von Komplexität und verwaltbarkeit von verwaltetem Code](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

 Ein niedriger Wartbarkeitsindex zeigt an, dass ein Typ oder Methode wahrscheinlich schwer zu verwalten und wäre ein guter Kandidat, neu zu entwerfen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um diese Verletzung zu beheben, gestalten Sie den Typ oder die Methode aus, und versuchen Sie es in kleinere und stärker fokussierte Typen oder Methoden unterteilt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Schließen Sie diese Warnung aus, wenn Sie einen Typ oder Methode immer noch als verwaltbar angesehen wird trotz seiner Größe, oder wenn der Typ oder Methode unterteilt werden kann.

## <a name="see-also"></a>Siehe auch
 [Verwaltbarkeitswarnungen](../code-quality/maintainability-warnings.md) [Messen von Komplexität und verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)

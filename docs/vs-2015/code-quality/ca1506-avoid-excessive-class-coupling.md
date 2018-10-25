---
title: 'CA1506: Übermäßige Klassenkopplungen vermeiden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 488d00b3277f4bf8cdc857f9c389348092f55bab
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939383"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Übermäßige Klassenkopplungen vermeiden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Kategorie|Microsoft.Maintainability|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ oder Methode ist mit vielen anderen Knotentypen gekoppelt.

## <a name="rule-description"></a>Regelbeschreibung
 Durch diese Regel wird die Klassenkopplung gemessen, indem die eindeutigen Typverweise, die ein Typ oder eine Methode enthält, gezählt werden.

 Typen und Methoden, die einen hohen Grad an Klassenkopplungen können schwierig zu verwalten sein. Es hat sich bewährt, Typen und Methoden, die lose Kopplung und hohe Kohäsion aufweisen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um diese Verletzung zu beheben, versuchen Sie, gestalten Sie den Typ oder eine Methode zum Verringern der Anzahl von Typen, mit denen er verknüpft ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Ausgeschlossen Sie diese Warnung, wenn der Typ oder die Methode weiterhin gewartet werden kann, trotz der großen Anzahl von Abhängigkeiten von anderen Typen betrachtet wird.

## <a name="see-also"></a>Siehe auch
 [Verwaltbarkeitswarnungen](../code-quality/maintainability-warnings.md) [Messen von Komplexität und verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)




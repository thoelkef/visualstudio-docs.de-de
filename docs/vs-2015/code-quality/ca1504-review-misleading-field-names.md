---
title: 'CA1504: Irreführende Feldnamen überprüfen | Microsoft-Dokumentation'
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
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c927457e2e16f19c221204ba445dad6c127da850
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878387"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Irreführende Feldnamen überprüfen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Kategorie|Microsoft.Maintainability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Der Name eines Instanzenfelds beginnt mit "S_" oder den Namen einer `static` (`Shared` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) Feld beginnt mit "M_".

## <a name="rule-description"></a>Regelbeschreibung
 Feldnamen, die mit "S_" beginnen, sind statische Daten von vielen Benutzern zugeordnet. Auf ähnliche Weise werden die Feldnamen, die mit "M_" beginnen (Member) Instanzdaten zugeordnet. Für Code einfacher zu verwalten sollten Namen in der Regel verwendeten Konventionen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, benennen Sie das Feld mit dem entsprechenden Präfix. Alternativ passen Sie das Feld mit dem aktuellen Suffix durch Hinzufügen oder Entfernen der `static` Modifizierer.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.




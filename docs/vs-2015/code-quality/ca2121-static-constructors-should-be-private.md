---
title: 'CA2121: Statische Konstruktoren sollten privat sein | Microsoft-Dokumentation'
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
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6b7052a25df5e736276b458247eb625ab584d473
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589604"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Statische Konstruktoren sollten privat sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA2121: statische Konstruktoren sollten privat sein](https://docs.microsoft.com/visualstudio/code-quality/ca2121-static-constructors-should-be-private).

|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ hat einen statischen Konstruktor, der nicht privat ist.

## <a name="rule-description"></a>Regelbeschreibung
 Ein statischer Konstruktor auch einen Klassenkonstruktor, wird verwendet, um einen Typ zu initialisieren. Das System ruft den statischen Konstruktor auf, bevor die erste Instanz des Typs erzeugt wird bzw. bevor auf irgendwelche statischen Member verwiesen wird. Der Benutzer hat keine Kontrolle darüber, wenn der statische Konstruktor aufgerufen wird. Wenn ein statischer Konstruktor nicht privat ist, kann er von Code aufgerufen werden, der nicht Systemcode ist. Je nach den Operationen innerhalb des Konstruktors kann dies zu unerwartetem Verhalten führen.

 Mit dieser Regel wird durch die C#- und Visual Basic-Compiler erzwungen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Verstöße gegen werden in der Regel durch eine der folgenden Aktionen verursacht:

-   Sie definiert einen statischen Konstruktor für den Typ und nicht, ihn als privat.

-   Programmierung Sprachcompilers, die einen statischen Standardkonstruktor in den Typ hinzugefügt und nicht, ihn als privat.

 Um die erste Art von Verstoß zu beheben, stellen Sie Ihre statischen Konstruktor private. Um die zweite Art zu beheben, fügen Sie einen privaten statischen Konstruktor in den Typ aus.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Verletzungen. Wenn Ihres Softwaredesigns einen expliziten Aufruf an einen statischen Konstruktor erforderlich ist, ist es wahrscheinlich, dass der Entwurf schwerwiegenden Fehler enthält und überprüft werden.




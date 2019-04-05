---
title: 'CA2121: Statische Konstruktoren sollten privat sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
ms.openlocfilehash: d7894b4ec0039b28a579239605c22c2397c300f3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947029"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Statische Konstruktoren sollten privat sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

- Sie definiert einen statischen Konstruktor für den Typ und nicht, ihn als privat.

- Programmierung Sprachcompilers, die einen statischen Standardkonstruktor in den Typ hinzugefügt und nicht, ihn als privat.

  Um die erste Art von Verstoß zu beheben, stellen Sie Ihre statischen Konstruktor private. Um die zweite Art zu beheben, fügen Sie einen privaten statischen Konstruktor in den Typ aus.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Verletzungen. Wenn Ihres Softwaredesigns einen expliziten Aufruf an einen statischen Konstruktor erforderlich ist, ist es wahrscheinlich, dass der Entwurf schwerwiegenden Fehler enthält und überprüft werden.

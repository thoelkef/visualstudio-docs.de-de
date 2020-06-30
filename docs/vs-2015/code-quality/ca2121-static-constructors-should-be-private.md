---
title: 'CA2121: statische Konstruktoren sollten privat sein | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f95b33e1391ca755a6c0df261fa2bd05bd3c7a0
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544312"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121: Statische Konstruktoren sollten privat sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ verfügt über einen statischen Konstruktor, der nicht privat ist.

## <a name="rule-description"></a>Beschreibung der Regel
 Ein statischer Konstruktor, der auch als Klassenkonstruktor bezeichnet wird, wird verwendet, um einen Typ zu initialisieren. Das System ruft den statischen Konstruktor auf, bevor die erste Instanz des Typs erzeugt wird bzw. bevor auf irgendwelche statischen Member verwiesen wird. Der Benutzer hat keine Kontrolle darüber, wann der statische Konstruktor aufgerufen wird. Wenn ein statischer Konstruktor nicht privat ist, kann er von Code aufgerufen werden, der nicht Systemcode ist. Je nach den Operationen innerhalb des Konstruktors kann dies zu unerwartetem Verhalten führen.

 Diese Regel wird von den c#-und Visual Basic .NET-Compilern erzwungen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Verstöße werden in der Regel durch eine der folgenden Aktionen verursacht:

- Sie haben einen statischen Konstruktor für den Typ definiert und ihn nicht als privat festgelegt.

- Der Programmiersprachen Compiler hat dem Typ einen statischen Standardkonstruktor hinzugefügt und ihn nicht als privat eingestellt.

  Legen Sie den statischen Konstruktor als privat fest, um die erste Art von Verstoß zu beheben. Um die zweite Art zu beheben, fügen Sie dem Typ einen privaten statischen Konstruktor hinzu.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie diese Verstöße nicht. Wenn Ihr Software Entwurf einen expliziten Aufrufvorgang eines statischen Konstruktors erfordert, ist es wahrscheinlich, dass der Entwurf ernsthafte Mängel enthält und überprüft werden sollte.

---
title: 'CA1725: Parameternamen sollten mit der Basisdeklaration übereinstimmen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d3564f3713dd24488e71703e902ae63f09b6aa74
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: Parameternamen sollten mit der Basisdeklaration übereinstimmen
|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name eines Parameters in einer Überschreibung extern sichtbare Methode entspricht nicht den Namen des Parameters in der Basisdeklaration der Methode oder den Namen des Parameters in der Schnittstellendeklaration der Methode.

## <a name="rule-description"></a>Regelbeschreibung
 Die konsistente Benennung von Parametern in einer Überschreibungshierarchie erhöht die Verwendbarkeit von Methodenüberschreibungen. Ein Parametername in einer abgeleiteten Methode, der vom Namen in der Basisdeklaration abweicht, kann zu Unklarheiten dahingehend führen, ob es sich bei der Methode um eine Überschreibung der Basismethode oder eine neue Überladung der Methode handelt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, benennen Sie den Parameter, um der Basisdeklaration übereinstimmen. Die Korrektur besteht eine wichtige Änderung für COM sichtbare Methoden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, mit Ausnahme von COM-sichtbaren Methoden in Bibliotheken, die zuvor versendet habe.
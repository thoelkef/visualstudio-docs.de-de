---
title: 'CA1725: Parameter Namen sollten mit der Basis Deklaration identisch sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 128069bb24dfc8b1c11963e33c9541701b0eea15
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653738"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: Parameternamen sollten mit der Basisdeklaration übereinstimmen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name eines Parameters in einer extern sichtbaren Methoden Überschreibung stimmt nicht mit dem Namen des Parameters in der Basis Deklaration der Methode oder mit dem Namen des Parameters in der Schnittstellen Deklaration der Methode.

## <a name="rule-description"></a>Regelbeschreibung
 Die konsistente Benennung von Parametern in einer Überschreibungshierarchie erhöht die Verwendbarkeit von Methodenüberschreibungen. Ein Parametername in einer abgeleiteten Methode, der vom Namen in der Basisdeklaration abweicht, kann zu Unklarheiten dahingehend führen, ob es sich bei der Methode um eine Überschreibung der Basismethode oder eine neue Überladung der Methode handelt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, benennen Sie den Parameter so um, dass er der Basis Deklaration entspricht. Die Korrektur ist eine Breaking Change für sichtbare com-Methoden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, außer für COM-sichtbare Methoden in Bibliotheken, die zuvor ausgeliefert wurden.

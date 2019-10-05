---
title: 'CA1725: Parameternamen sollten mit der Basisdeklaration übereinstimmen | Microsoft-Dokumentation'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e97431b46640fb8241d6bde80d09d38084650be8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143172"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: Parameternamen sollten mit der Basisdeklaration übereinstimmen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name eines Parameters in einer Außerkraftsetzung extern sichtbare Methode entspricht nicht den Namen des Parameters in der Basisdeklaration der Methode oder den Namen des Parameters in der Schnittstellendeklaration der Methode.

## <a name="rule-description"></a>Regelbeschreibung
 Die konsistente Benennung von Parametern in einer Überschreibungshierarchie erhöht die Verwendbarkeit von Methodenüberschreibungen. Ein Parametername in einer abgeleiteten Methode, der vom Namen in der Basisdeklaration abweicht, kann zu Unklarheiten dahingehend führen, ob es sich bei der Methode um eine Überschreibung der Basismethode oder eine neue Überladung der Methode handelt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, benennen Sie die Parameter, um mit der der Basisdeklaration übereinstimmen. Die Lösung ist eine wichtige Änderung für COM sichtbare Methoden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, mit Ausnahme von COM-sichtbare Methoden in Bibliotheken, die zuvor veröffentlicht haben.

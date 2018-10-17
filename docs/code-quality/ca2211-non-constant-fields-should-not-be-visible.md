---
title: 'CA2211: Nicht konstante Felder sollten nicht sichtbar sein'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0e40065351342ab49b86b21bb525b45ce78c6028
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550545"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: Nicht konstante Felder sollten nicht sichtbar sein

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschütztes statisches Feld ist nicht konstant. noch ist es schreibgeschützt.

## <a name="rule-description"></a>Regelbeschreibung
 Statische Felder, die weder konstant noch schreibgeschützt sind, sind nicht threadsicher. Zugriff auf ein solches Feld muss sorgfältig kontrolliert und erfordert fortgeschrittene Programmiertechniken zur Synchronisierung des Zugriffs auf das Klassenobjekt. Da hierbei handelt es sich um schwierig Fähigkeiten, um zu erfahren und Master und testen ein solches Objekt stellt eine eigene Herausforderungen, sind statische Felder am besten verwendet, zum Speichern von Daten, die nicht geändert wird. Diese Regel gilt für Bibliotheken. Anwendungen sollten keine Felder verfügbar machen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie das statische Feld, konstant oder schreibgeschützt. Wenn dies nicht möglich ist, ändern Sie den Typ um einen alternativen Mechanismus wie z. B. eine Thread-sichere-Eigenschaft verwenden, die threadsicheren Zugriff auf das zugrunde liegende Feld verwaltet. Beachten Sie, dass Probleme, z. B. Sperrenkonflikte und Deadlocks die Leistung und das Verhalten der Bibliothek auswirken können.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, unterdrücken Sie eine Warnung dieser Regel ein, wenn Sie eine Anwendung entwickeln und aus diesem Grund haben vollständige Kontrolle über Zugriff auf den Typ mit dem statischen Feld. Bibliotheks-Designer sollte eine Warnung dieser Regel nicht unterdrückt werden; nicht konstante statische Felder verwenden, kann die unter Verwendung der Bibliothek, die schwierig für Entwickler für die ordnungsgemäße Verwendung vornehmen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen diese Regel verstößt.

 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]
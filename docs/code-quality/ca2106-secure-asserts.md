---
title: 'CA2106: Sichere Bestätigungen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c8d80c4e9a21c29ce7b34a3998e241b11713f355
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545699"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Sichere Bestätigungen.

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode bestätigt eine Berechtigung an, und führt keine sicherheitsüberprüfungen für den Aufrufer.

## <a name="rule-description"></a>Regelbeschreibung
 Das Gewähren einer Sicherheitsberechtigung ohne Sicherheitsüberprüfungen durchzuführen, kann ein ausnutzbares Sicherheitsrisiko in Code hinterlassen. Ein Sicherheitsstackwalk wird beendet, wenn eine Sicherheitsberechtigung gewährt wird. Wenn Sie eine Berechtigung ohne jegliche Überprüfung des Aufrufers gewähren, kann der Aufrufer indirekt Code ausführen, mithilfe Ihrer Berechtigungen. Assert-Vorgänge ohne sicherheitsüberprüfungen sind zulässig, wenn Sie sind Sie sicher, dass die Assertion auf schädliche Weise verwendet werden kann. Assert ist harmlos, wenn der Code, den Sie aufrufen, harmlos ist oder wenn Benutzer willkürlichen Informationen an Code übergeben können, die Sie aufrufen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der Methode oder der deklarierende Typ eine sicherheitsforderung hinzu.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel erst nach einer sorgfältigen sicherheitsreview.

## <a name="see-also"></a>Siehe auch

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- [Richtlinien für das Schreiben von sicherem Code](/dotnet/standard/security/secure-coding-guidelines)
---
title: 'CA2106: Sichere Bestätigungen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 164d2bbe335f4b69892cf069bade5cf0df1e0787
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864672"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Sichere Bestätigungen

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
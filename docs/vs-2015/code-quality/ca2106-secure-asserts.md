---
title: 'CA2106: Sichere Bestätigungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1f333478c952db74fa6a9482cdad91ce6a858301
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665996"
---
# <a name="ca2106-secure-asserts"></a>CA2106: Sichere Bestätigungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode bestätigt eine Berechtigung, und es werden keine Sicherheitsüberprüfungen für den Aufrufer durchgeführt.

## <a name="rule-description"></a>Regelbeschreibung
 Das Gewähren einer Sicherheitsberechtigung ohne Sicherheitsüberprüfungen durchzuführen, kann ein ausnutzbares Sicherheitsrisiko in Code hinterlassen. Ein Sicherheits Stapel-Walk wird beendet, wenn eine Sicherheits Berechtigung bestätigt wird. Wenn Sie eine Berechtigung ohne Überprüfung des Aufrufers bestätigen, könnte der Aufrufer indirekt Code ausführen, indem er ihre Berechtigungen verwendet. Bestätigungen ohne Sicherheitsüberprüfungen sind nur zulässig, wenn Sie sicher sind, dass Assert nicht schädlich verwendet werden kann. Eine Assert-Bestätigung ist harmlos, wenn der aufzurufende Code harmlos ist oder wenn Benutzer keine willkürlichen Informationen an den von Ihnen aufzurufenden Code übergeben können

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der Methode oder dem deklarierenden Typ eine Sicherheitsanforderung hinzu.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel erst nach einer sorgfältigen Sicherheitsüberprüfung.

## <a name="see-also"></a>Siehe auch
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [sichere Codierungs Richtlinien](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)

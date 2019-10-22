---
title: 'CA2103: imperative Sicherheit überprüfen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b4abf0b15a4fbba1abc61572da8a2f6126c754f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652160"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Imperative Sicherheit überprüfen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode verwendet imperative Sicherheit und erstellt möglicherweise die Berechtigung mit Zustandsinformationen oder Rückgabewerten, die sich ändern können, während die Forderung wirksam ist.

## <a name="rule-description"></a>Regelbeschreibung
 Bei imperativer Sicherheit werden verwaltete Objekte verwendet, um während der Codeausführung Berechtigungen und Sicherheitsaktionen anzugeben, im Vergleich zur deklarativen Sicherheit, bei der Attribute verwendet werden, um Berechtigungen und Aktionen in Metadaten zu speichern. Imperative Sicherheit ist sehr flexibel, da Sie den Status eines Berechtigungs Objekts festlegen und Sicherheitsaktionen mithilfe von Informationen auswählen können, die bis zur Laufzeit nicht verfügbar sind. Mit dieser Flexibilität besteht das Risiko, dass die Laufzeitinformationen, mit denen Sie den Zustand einer Berechtigung ermitteln, unverändert bleiben, solange die Aktion wirksam ist.

 Verwenden Sie, wenn irgend möglich, deklarative Sicherheit. Deklarative Anforderungen sind leichter zu verstehen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Überprüfen Sie die imperative Sicherheitsanforderungen, um sicherzustellen, dass sich der Status der Berechtigung nicht auf Informationen stützt, die sich ändern können, solange die Berechtigung verwendet wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn sich die Berechtigung nicht auf das Ändern von Daten verlässt. Es ist jedoch besser, den imperativen Bedarf in seine deklarative Entsprechung zu ändern.

## <a name="see-also"></a>Siehe auch
 [Daten und Modellierung](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) für [sichere Codierungs Richtlinien](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)

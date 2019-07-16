---
title: 'CA2103: Imperative Sicherheit überprüfen | Microsoft-Dokumentation'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5b8b3067d5c8ab8204d6ad723315c400e7b27552
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694926"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Imperative Sicherheit überprüfen.
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
 Imperativer Sicherheit verwendet verwaltete Objekte angeben, Berechtigungen und Sicherheitsaktionen während der codeausführung, im Vergleich zu deklarative Sicherheit, der Attribute verwendet, um Berechtigungen und Aktionen in den Metadaten zu speichern. Imperativer Sicherheit ist sehr flexibel, da es sich bei den Zustand eines Objekts Berechtigungen festlegen und wählen Sie die Sicherheitsaktionen mithilfe von Informationen, die bis zur Laufzeit nicht verfügbar ist. Zusammen mit, die aber auch Flexibilität das Risiko, das die Runtime-Informationen, die Sie verwenden, um zu bestimmen, dass der Zustand einer Berechtigung nicht bleibt unverändert, solange die Aktion ausgeführt wird.

 Verwenden Sie, wenn irgend möglich, deklarative Sicherheit. Deklarative Befehle sind einfacher zu verstehen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Überprüfen Sie die Anforderungen imperative Sicherheit, um sicherzustellen, dass der Zustand der Berechtigung nicht auf den Informationen abhängig ist, die sich ändern können, solange die Berechtigung verwendet wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn die Berechtigung zum Ändern von Daten nicht abhängig ist. Allerdings ist es besser, die die imperative Forderung in den entsprechenden deklarative zu ändern.

## <a name="see-also"></a>Siehe auch
 [Sichern Sie die Richtlinien für das Codieren](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Daten und Modellierung](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)

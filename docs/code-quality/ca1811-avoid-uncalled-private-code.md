---
title: 'CA1811: Nicht aufgerufenen privaten Code vermeiden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b8c71c7dc549c980be8ae7a2241629774f32150
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822970"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Nicht aufgerufenen privaten Code vermeiden

|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein privater oder interner Member der (auf Assemblyebene) in der Assembly keine Aufrufer, wird nicht von der common Language Runtime aufgerufen und nicht durch einen Delegaten aufgerufen. Die folgenden Member werden nicht durch diese Regel überprüft:

- Auf explizite Schnittstellenmember.

- Statische Konstruktoren.

- Serialisierungskonstruktoren.

- Mit markierte Methoden <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> oder <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

- Elemente, die Außerkraftsetzungen sind.

## <a name="rule-description"></a>Regelbeschreibung
 Mit dieser Regel Berichts kann falsch positive Ergebnisse, wenn Einstiegspunkte, die auftreten, von der Regellogik derzeit nicht identifiziert werden. Darüber hinaus kann ein Compiler nicht aufrufbaren Code in eine Assembly ausgeben.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den Code nicht aufrufbaren, oder fügen Sie Code, den sie aufruft.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, unterdrücken Sie eine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)
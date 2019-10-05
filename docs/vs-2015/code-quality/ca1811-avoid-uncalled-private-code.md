---
title: 'CA1811: Nicht aufgerufenen privaten Code vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 373ccaa6552079a8995d61ef09bf6e0845c299d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157966"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Nicht aufgerufenen privaten Code vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, unterdrücken Sie eine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Nicht verwendete Parameter überprüfen](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)

---
title: 'CA1811: nicht aufgerufenen privaten Code vermeiden | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 223b2ff9aa25ddd94a3c62eb9e641127a1cace4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543818"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: Nicht aufgerufenen privaten Code vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Category|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein privater oder interner Member (auf Assemblyebene) besitzt keine Aufrufer in der Assembly, wird nicht vom Common Language Runtime aufgerufen und wird nicht von einem Delegaten aufgerufen. Folgende Mitglieder werden von dieser Regel nicht geprüft:

- Explizite Schnittstellenmember.

- Statische Konstruktoren.

- Serialisierungskonstruktoren.

- Mit oder gekennzeichnete Methoden <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> .

- Member, die außer Kraft gesetzt werden.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel kann falsch positive Ergebnisse melden, wenn Einstiegspunkte auftreten, die derzeit nicht durch die Regellogik identifiziert werden. Außerdem kann ein Compiler nicht Aufruf baren Code in eine Assembly ausgeben.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den nicht Aufruf baren Code, oder fügen Sie Code hinzu, der ihn aufruft.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1812: Nicht instanziierte interne Klassen vermeiden.](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: Nicht verwendete Parameter überprüfen.](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: Nicht verwendete lokale Variablen entfernen.](../code-quality/ca1804-remove-unused-locals.md)

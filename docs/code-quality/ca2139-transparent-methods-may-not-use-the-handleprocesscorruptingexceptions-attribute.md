---
title: 'CA2139: Transparente Methoden dürfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 786fc64eb8ce7bd52ddfbb36587f9f944bf0d734
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548451"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: Transparente Methoden dürfen das HandleProcessCorruptingExceptions-Attribut nicht verwenden
|||
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine transparente Methode ist mit markiert die <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> Attribut.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird ausgelöst, eine Methode, die transparent ist und versucht, eine prozessdestabilisierende Ausnahme mit behandeln die <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> Attribut. Eine prozessdestabilisierende Ausnahme ist eine CLR-Version 4.0 Ausnahme Klassifizierung von Ausnahmen, die solche <xref:System.AccessViolationException>. Das HandleProcessCorruptedStateExceptionsAttribute-Attribut darf nur von sicherheitskritischen Methoden verwendet werden und wird ignoriert, wenn es für eine transparente Methode übernommen wird. Zum Prozess Beschädigung Ausnahmen zu behandeln, muss diese Methode sicherheitskritisch oder sicherheitsgeschützt sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen die <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> Attribut, oder markieren Sie die Methode mit dem <xref:System.Security.SecurityCriticalAttribute> oder <xref:System.Security.SecuritySafeCriticalAttribute> Attribut.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 In diesem Beispiel ist eine transparente Methode mit markiert die <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> Attribut, und die Regel fehl. Die Methode sollte mit gekennzeichnet werden die <xref:System.Security.SecurityCriticalAttribute> oder <xref:System.Security.SecuritySafeCriticalAttribute> Attribut.

 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]
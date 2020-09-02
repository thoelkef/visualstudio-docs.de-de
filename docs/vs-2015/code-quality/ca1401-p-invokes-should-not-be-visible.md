---
title: 'CA1401: P-Aufrufe dürfen nicht sichtbar sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9f13669959a5874c74753d304371b8ab7db14d4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547289"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invokes dürfen nicht sichtbar sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Category|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ weist das- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> Attribut auf (auch durch das- `Declare` Schlüsselwort implementiert [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

## <a name="rule-description"></a>Beschreibung der Regel
 Methoden, die mit dem- <xref:System.Runtime.InteropServices.DllImportAttribute> Attribut markiert sind (oder Methoden, die mit dem- `Declare` Schlüsselwort in definiert werden), [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] verwenden Platt Form Aufruf Dienste für den Zugriff auf nicht verwalteten Code. Solche Methoden sollten nicht verfügbar gemacht werden. Wenn Sie diese Methoden als privat oder intern aufbewahren, stellen Sie sicher, dass die Bibliothek nicht zum verletzen der Sicherheit verwendet werden kann, indem Sie Aufrufern Zugriff auf nicht verwaltete APIs gewähren, die nicht anderweitig aufgerufen werden konnten.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Zugriffsebene der Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird eine Methode deklariert, die gegen diese Regel verstößt.

 [!code-csharp[FxCop.Interoperability.DllImports#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/cs/FxCop.Interoperability.DllImports.cs#1)]
 [!code-vb[FxCop.Interoperability.DllImports#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/vb/FxCop.Interoperability.DllImports.vb#1)]

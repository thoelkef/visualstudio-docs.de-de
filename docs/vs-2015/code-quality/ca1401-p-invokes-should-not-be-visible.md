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
ms.openlocfilehash: f3f867f14f7a2eca4482f1f8d5fb48149f02f43f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661358"
---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invokes dürfen nicht sichtbar sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokesShouldNotBeVisible|
|CheckId|CA1401|
|Kategorie|Microsoft. Interoperabilität|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ verfügt über das <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>-Attribut (auch durch das `Declare`-Schlüsselwort in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] implementiert).

## <a name="rule-description"></a>Regelbeschreibung
 Methoden, die mit dem <xref:System.Runtime.InteropServices.DllImportAttribute>-Attribut gekennzeichnet sind (oder Methoden, die mithilfe des Schlüssel Worts `Declare` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] definiert werden), verwenden Platt Form Aufruf Dienste, um auf nicht verwalteten Code zuzugreifen. Solche Methoden sollten nicht verfügbar gemacht werden. Wenn Sie diese Methoden als privat oder intern aufbewahren, stellen Sie sicher, dass die Bibliothek nicht zum verletzen der Sicherheit verwendet werden kann, indem Sie Aufrufern Zugriff auf nicht verwaltete APIs gewähren, die nicht anderweitig aufgerufen werden konnten.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Zugriffsebene der Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird eine Methode deklariert, die gegen diese Regel verstößt.

 [!code-csharp[FxCop.Interoperability.DllImports#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/cs/FxCop.Interoperability.DllImports.cs#1)]
 [!code-vb[FxCop.Interoperability.DllImports#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DllImports/vb/FxCop.Interoperability.DllImports.vb#1)]

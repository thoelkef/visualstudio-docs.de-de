---
title: 'CA2232: Windows Forms Einstiegspunkte mit STAThread markieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 42bb554f8e57c036d41a89fdc2657a25ecc74e20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540282"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Windows Forms-Einstiegspunkte mit STAThread markieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Assembly verweist auf den <xref:System.Windows.Forms> Namespace, und der Einstiegspunkt ist nicht mit dem- <xref:System.STAThreadAttribute?displayProperty=fullName> Attribut gekennzeichnet.

## <a name="rule-description"></a>Beschreibung der Regel
 <xref:System.STAThreadAttribute> Gibt an, dass das COM-Threading Modell für die Anwendung ein Single Thread-Apartment ist. Dieses Attribut muss am Einstiegspunkt jeder Anwendung vorhanden sein, die Windows Forms verwendet. Wird es weggelassen, funktionieren die Windows-Komponenten eventuell nicht richtig. Wenn das-Attribut nicht vorhanden ist, verwendet die Anwendung das Multithread Apartment-Modell, das für Windows Forms nicht unterstützt wird.

> [!NOTE]
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Projekte, in denen das Anwendungs Framework verwendet wird, müssen die **Main** -Methode nicht mit STAThread markieren. Der [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Compiler führt dies automatisch aus.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie dem <xref:System.STAThreadAttribute> Einstiegspunkt das-Attribut hinzu. Wenn das <xref:System.MTAThreadAttribute?displayProperty=fullName> Attribut vorhanden ist, entfernen Sie es.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn Sie für die .NET Compact Framework entwickeln, für die das <xref:System.STAThreadAttribute> Attribut unnötig ist und nicht unterstützt wird.

## <a name="example"></a>Beispiel
 In den folgenden Beispielen wird die korrekte Verwendung von veranschaulicht <xref:System.STAThreadAttribute> .

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]

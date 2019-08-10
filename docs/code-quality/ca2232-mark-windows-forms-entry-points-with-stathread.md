---
title: 'CA2232: Windows Forms-Einstiegspunkte mit STAThread markieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: dd3f5b76015a3a54ee085b5cc2dd532920ff0795
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920173"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Windows Forms-Einstiegspunkte mit STAThread markieren.

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
Eine Assembly verweist auf <xref:System.Windows.Forms> den Namespace, und der Einstiegspunkt ist nicht mit dem <xref:System.STAThreadAttribute?displayProperty=fullName> -Attribut gekennzeichnet.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.STAThreadAttribute>Gibt an, dass das COM-Threading Modell für die Anwendung ein Single Thread-Apartment ist. Dieses Attribut muss am Einstiegspunkt jeder Anwendung vorhanden sein, die Windows Forms verwendet. Wird es weggelassen, funktionieren die Windows-Komponenten eventuell nicht richtig. Wenn das-Attribut nicht vorhanden ist, verwendet die Anwendung das Multithread Apartment-Modell, das für Windows Forms nicht unterstützt wird.

> [!NOTE]
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]Projekte, in denen das Anwendungs Framework verwendet wird, müssen die **Main** -Methode nicht mit STAThread markieren. Der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Compiler führt dies automatisch aus.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, fügen <xref:System.STAThreadAttribute> Sie dem Einstiegspunkt das-Attribut hinzu. Wenn das <xref:System.MTAThreadAttribute?displayProperty=fullName> Attribut vorhanden ist, entfernen Sie es.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn Sie für die .NET Compact Framework entwickeln, für <xref:System.STAThreadAttribute> die das Attribut unnötig ist und nicht unterstützt wird.

## <a name="example"></a>Beispiel
In den folgenden Beispielen wird die korrekte Verwendung <xref:System.STAThreadAttribute>von veranschaulicht:

[!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
[!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]
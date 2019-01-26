---
title: 'CA2232: Windows Forms-Einstiegspunkte mit STAThread markieren.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 1ee37645d1cc20bfd83a18b9dbb7a001731702f1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2019
ms.locfileid: "55043673"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Windows Forms-Einstiegspunkte mit STAThread markieren.

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine Assembly verweist auf die <xref:System.Windows.Forms> Namespace und der Einstiegspunkt ist nicht mit markiert die <xref:System.STAThreadAttribute?displayProperty=fullName> Attribut.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.STAThreadAttribute> Gibt an, dass das COM-Threadingmodell für die Anwendung Singlethread-Apartment. Dieses Attribut muss am Einstiegspunkt jeder Anwendung vorhanden sein, die Windows Forms verwendet. Wird es weggelassen, funktionieren die Windows-Komponenten eventuell nicht richtig. Wenn das Attribut nicht vorhanden ist, verwendet die Anwendung die Multithread-Apartment-Modell, die für Windows Forms nicht unterstützt wird.

> [!NOTE]
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Projekte, die das Anwendungsframework verwendet keine markieren die **Main** Methode mit STAThread markieren. Die [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Compiler automatisch durchführt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen die <xref:System.STAThreadAttribute> -Attribut auf den Einstiegspunkt. Wenn die <xref:System.MTAThreadAttribute?displayProperty=fullName> Attribut vorhanden ist, entfernen Sie sie.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicherer, unterdrücken Sie eine Warnung dieser Regel ein, wenn Sie für .NET Compact Framework, für das Entwickeln der <xref:System.STAThreadAttribute> -Attribut ist nicht erforderlich und wird nicht unterstützt.

## <a name="example"></a>Beispiel
 Die folgenden Beispiele veranschaulichen die richtige Verwendung von <xref:System.STAThreadAttribute>:

 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]
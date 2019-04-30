---
title: 'CA2232: Mark Windows Forms-Einstiegspunkte mit STAThread markieren | Microsoft-Dokumentation'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6e8b7242fcd82db1a0cfb82cf6cd6df5a9f75084
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435413"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: Windows Forms-Einstiegspunkte mit STAThread markieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Projekte, die das Anwendungsframework verwendet keine markieren die **Main** Methode mit STAThread markieren. Die [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Compiler automatisch durchführt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen die <xref:System.STAThreadAttribute> -Attribut auf den Einstiegspunkt. Wenn die <xref:System.MTAThreadAttribute?displayProperty=fullName> Attribut vorhanden ist, entfernen Sie sie.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicherer, unterdrücken Sie eine Warnung dieser Regel ein, wenn Sie für .NET Compact Framework, für das Entwickeln der <xref:System.STAThreadAttribute> -Attribut ist nicht erforderlich und wird nicht unterstützt.

## <a name="example"></a>Beispiel
 Die folgenden Beispiele veranschaulichen die richtige Verwendung von <xref:System.STAThreadAttribute>.

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]

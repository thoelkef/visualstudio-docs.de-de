---
title: 'CA1300: MessageBoxOptions angeben'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 815fe7b7f839adeb3204e33bb532b70909d92b53
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056386"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: MessageBoxOptions angeben

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Methode aufruft, eine Überladung von der <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> Methode, die keine <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> Argument.

## <a name="rule-description"></a>Regelbeschreibung

Ein Meldungsfeld an, für die Kulturen ordnungsgemäß anzeigen, die eine rechts-nach-Links-Lesefolge verwenden, übergeben die [MessageBoxOptions.RightAlign](<xref:System.Windows.Forms.MessageBoxOptions.RightAlign>) und [MessageBoxOptions.RtlReading](<xref:System.Windows.Forms.MessageBoxOptions.RtlReading>) Felder der <xref:System.Windows.Forms.MessageBox.Show%2A> -Methode. Überprüfen Sie die <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> Eigenschaft des Containersteuerelements, um festzustellen, ob eine rechts-nach-Links-Lesefolge verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, rufen Sie eine Überladung von der <xref:System.Windows.Forms.MessageBox.Show%2A> Methode, eine <xref:System.Windows.Forms.MessageBoxOptions> Argument.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher ist, eine Warnung dieser Regel zu unterdrücken, wenn die Codebibliothek nicht für eine Kultur lokalisiert wird, die eine rechts-nach-Links-Lesefolge verwendet.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Methode, die ein Meldungsfeld angezeigt, die Optionen, die für die leserichtung der Kultur geeignet sind. Eine Ressourcendatei, die nicht angezeigt wird, ist erforderlich, um das Beispiel zu erstellen. Führen Sie die Kommentare im Beispiel um das Beispiel ohne eine Ressourcendatei zu erstellen und die rechts-nach-links-Funktion zu testen.

[!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
[!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Ressourcen in Desktop-Apps (.NET Framework)](/dotnet/framework/resources/index)
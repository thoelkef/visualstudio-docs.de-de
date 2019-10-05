---
title: 'CA1300: MessageBoxOptions angeben.'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 746475e60bbe72c4ebfc51f13d0b2d4d0552ff62
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235193"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: MessageBoxOptions angeben.

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Methode ruft eine Überladung der <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> Methode auf, die kein <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> -Argument annimmt.

## <a name="rule-description"></a>Regelbeschreibung

Wenn Sie ein Meldungs Feld für Kulturen, die eine Lesereihenfolge von rechts nach Links verwenden, ordnungsgemäß anzeigen möchten, übergeben Sie die Felder [MessageBoxOptions. RightAlign](<xref:System.Windows.Forms.MessageBoxOptions.RightAlign>) und [MessageBoxOptions. RtlReading](<xref:System.Windows.Forms.MessageBoxOptions.RtlReading>) an die <xref:System.Windows.Forms.MessageBox.Show%2A> -Methode. Überprüfen <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> Sie die-Eigenschaft des enthaltenden Steuer Elements, um zu bestimmen, ob die Lesefolge von rechts nach Links verwendet werden soll.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, müssen Sie eine über <xref:System.Windows.Forms.MessageBox.Show%2A> Ladung der-Methode <xref:System.Windows.Forms.MessageBoxOptions> aufrufen, die ein-Argument annimmt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Code Bibliothek nicht für eine Kultur lokalisiert wird, in der die Lesefolge von rechts nach Links verwendet wird.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine-Methode, die ein Meldungs Feld mit Optionen anzeigt, die für die Lesereihenfolge der Kultur geeignet sind. Eine Ressourcen Datei, die nicht angezeigt wird, ist erforderlich, um das Beispiel zu erstellen. Befolgen Sie die Kommentare im Beispiel, um das Beispiel ohne eine Ressourcen Datei zu erstellen und die Funktion von rechts nach Links zu testen.

[!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
[!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Ressourcen in Desktop-Apps (.NET Framework)](/dotnet/framework/resources/index)
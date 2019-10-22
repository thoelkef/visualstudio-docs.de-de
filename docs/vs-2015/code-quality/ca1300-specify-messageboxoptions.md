---
title: 'CA1300: Angeben von MessageBoxOptions | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3e21866fce69f768d927882d3ddd47ae3e431265
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663605"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: MessageBoxOptions angeben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Kategorie|Microsoft. Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode ruft eine Überladung der <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> Methode auf, die kein <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> Argument annimmt.

## <a name="rule-description"></a>Regelbeschreibung
 Um ein Meldungs Feld für Kulturen, die eine Lesereihenfolge von rechts nach Links verwenden, ordnungsgemäß anzuzeigen, müssen die <xref:System.Windows.Forms.MessageBoxOptions>-und <xref:System.Windows.Forms.MessageBoxOptions> Member der <xref:System.Windows.Forms.MessageBoxOptions>-Enumeration an die <xref:System.Windows.Forms.MessageBox.Show%2A>-Methode übermittelt werden. Überprüfen Sie die <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName>-Eigenschaft des enthaltenden Steuer Elements, um zu bestimmen, ob die Lesefolge von rechts nach Links verwendet werden soll.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen Sie eine Überladung der <xref:System.Windows.Forms.MessageBox.Show%2A>-Methode aufrufen, die ein <xref:System.Windows.Forms.MessageBoxOptions> Argument annimmt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Code Bibliothek nicht für eine Kultur lokalisiert wird, in der die Lesefolge von rechts nach Links verwendet wird.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine-Methode, die ein Meldungs Feld mit Optionen anzeigt, die für die Lesereihenfolge der Kultur geeignet sind. Eine Ressourcen Datei, die nicht angezeigt wird, ist erforderlich, um das Beispiel zu erstellen. Befolgen Sie die Kommentare im Beispiel, um das Beispiel ohne eine Ressourcen Datei zu erstellen und die Funktion von rechts nach Links zu testen.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.Resources.ResourceManager?displayProperty=fullName> von [Ressourcen in Desktop-Apps](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)

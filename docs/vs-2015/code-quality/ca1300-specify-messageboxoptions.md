---
title: 'CA1300: MessageBoxOptions angeben | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 157cac1ddd200799b0362529c0a434086db77781
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49288924"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: MessageBoxOptions angeben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode aufruft, eine Überladung von der <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> Methode, die keine <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> Argument.

## <a name="rule-description"></a>Regelbeschreibung
 Ein Meldungsfeld an, für die Kulturen ordnungsgemäß angezeigt, die eine rechts-nach-Links-Lesefolge, verwenden die <xref:System.Windows.Forms.MessageBoxOptions> und <xref:System.Windows.Forms.MessageBoxOptions> Mitglied der <xref:System.Windows.Forms.MessageBoxOptions> Enumeration übergeben werden muss, um die <xref:System.Windows.Forms.MessageBox.Show%2A> Methode. Überprüfen Sie die <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> Eigenschaft des Containersteuerelements, um festzustellen, ob eine rechts-nach-Links-Lesefolge verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie eine Überladung von der <xref:System.Windows.Forms.MessageBox.Show%2A> Methode, eine <xref:System.Windows.Forms.MessageBoxOptions> Argument.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher ist, eine Warnung dieser Regel zu unterdrücken, wenn die Codebibliothek nicht für eine Kultur lokalisiert wird, die eine rechts-nach-Links-Lesefolge verwendet.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die ein Meldungsfeld angezeigt, die Optionen, die für die leserichtung der Kultur geeignet sind. Eine Ressourcendatei, die nicht angezeigt wird, ist erforderlich, um das Beispiel zu erstellen. Führen Sie die Kommentare im Beispiel um das Beispiel ohne eine Ressourcendatei zu erstellen und die rechts-nach-links-Funktion zu testen.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Ressourcen in Desktop-Apps](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)




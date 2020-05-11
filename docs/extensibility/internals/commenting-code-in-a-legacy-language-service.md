---
title: Kommentieren von Code in einem Legacy-Sprachdienst | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5450199fde29f581dafdf9b2884c88ef26ea4ce7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709442"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Kommentarcode in einem älteren Sprachdienst
Programmiersprachen bieten in der Regel eine Möglichkeit, den Code zu kommentieren oder zu kommentieren. Ein Kommentar ist ein Textabschnitt, der zusätzliche Informationen zum Code bereitstellt, aber während der Kompilierung oder Interpretation ignoriert wird.

 Die MPF-Klassen (Managed Package Framework) unterstützen das Kommentieren und Aufdecken von ausgewähltem Text.

## <a name="comment-styles"></a>Kommentarstile
Es gibt zwei allgemeine Arten von Kommentaren:

1. Zeilenkommentare, bei denen sich der Kommentar in einer einzigen Zeile befindet.

2. Blockieren Sie Kommentare, wobei der Kommentar mehrere Zeilen enthalten kann.

Zeilenkommentare haben in der Regel ein Startzeichen (oder Zeichen), während Blockkommentare sowohl Start- als auch Endzeichen haben. Ein Zeilenkommentar beginnt z. B. `//`mit , und `/*` ein Blockkommentar beginnt mit und endet mit `*/`.

Wenn der Benutzer den Befehl **Kommentarauswahl** aus dem Menü **Erweiterte Bearbeiten** > **Advanced** auswählt, wird der Befehl an die <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> Methode in der <xref:Microsoft.VisualStudio.Package.Source> Klasse weitergeleitet. Wenn der Benutzer den Befehl **Auswahl aufsuchen**auswählt, <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> wird der Befehl an die Methode weitergeleitet.

## <a name="support-code-comments"></a>Support-Codekommentare
 Sie können Codekommentare für Den Sprachdienst `EnableCommenting` mit Hilfe <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> des benannten Parameters der verwenden. Dadurch wird <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Eigenschaft der Klasse festgelegt. Weitere Informationen zum Festlegen von Sprachdienstfeatures finden Sie unter [Registrieren eines älteren Sprachdienstes](../../extensibility/internals/registering-a-legacy-language-service1.md).

 Sie müssen auch <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> die Methode <xref:Microsoft.VisualStudio.Package.CommentInfo> überschreiben, um eine Struktur mit den Kommentarzeichen für Ihre Sprache zurückzugeben. Zeilenkommentarzeichen im C-Stil sind die Standardzeichen.

### <a name="example"></a>Beispiel
 Hier ist ein Beispiel <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> für die Implementierung der Methode.

```csharp
using Microsoft.VisualStudio.Package;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override CommentInfo GetCommentFormat() {
            CommentInfo info = new CommentInfo();
            info.LineStart       = "//";
            info.BlockStart      = "/*";
            info.BlockEnd        = "*/";
            info.UseLineComments = true;
            return info;
        }
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [Legacy-Sprachdienstfunktionen](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrieren eines älteren Sprachdienstes](../../extensibility/internals/registering-a-legacy-language-service1.md)

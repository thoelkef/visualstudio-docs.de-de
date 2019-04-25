---
title: Kommentieren von Code in einem Legacysprachdienst | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c82669ac6d4f32f1525b7e14427ed620a51cfc5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102704"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Kommentieren von Code in einem legacy-Sprachdienst
Programmiersprachen bieten in der Regel eine Möglichkeit zum Kommentieren oder kommentieren Sie den Code. Ein Kommentar ist einen Textabschnitt, der enthält zusätzliche Informationen zu den Code wird jedoch ignoriert, während der Kompilierung oder Interpretation erfordern.

 Die verwaltete Package Framework (MPF)-Klassen bieten Unterstützung für auskommentieren und Aufheben der auskommentierung markierten Text.

## <a name="comment-styles"></a>Kommentarstile
Es gibt zwei allgemeine Arten der Kommentar:

1. Zeilenkommentare, die der Kommentar, in dem in einer einzelnen Zeile ist.

2. Block-Kommentare, in dem der Kommentar auf mehrere Zeilen enthalten kann.

Zeilenkommentare haben in der Regel ein (oder die Anfangszeichen), während blockskommentaren sowohl Start-und Endzeichen haben. In c# ein Zeilenkommentar starten z. B. mit `//`, und ein blockskommentar beginnt mit `/*` und endet mit `*/`.

Wenn der Benutzer den Befehl auswählt **Auswahl kommentieren** aus der **bearbeiten** > **erweitert** im Menü der Befehl geleitet wird die <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> Methode für die <xref:Microsoft.VisualStudio.Package.Source> Klasse. Wenn der Benutzer den Befehl auswählt **Kommentar der Auswahl**, der Befehl weitergeleitet wird, um die <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> Methode.

## <a name="support-code-comments"></a>Unterstützung von Kommentaren im code
 Sie haben Ihre Language Service Support Codekommentare von der `EnableCommenting` benannter Parameter, der die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Hiermit wird die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> Eigenschaft der <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse. Weitere Informationen zum Festlegen von Sprache-Service-Features finden Sie unter [Registrieren von Diensten legacysprache](../../extensibility/internals/registering-a-legacy-language-service1.md).

 Müssen Sie auch überschreiben die <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> -Methode zur Rückgabe einer <xref:Microsoft.VisualStudio.Package.CommentInfo> Struktur mit die Kommentarzeichen für Ihre Sprache. C#-Stil zeilenkommentarzeichen sind die Standardeinstellungen.

### <a name="example"></a>Beispiel
 Hier ist eine Beispiel einer Implementierung der <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> Methode.

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

## <a name="see-also"></a>Siehe auch
- [Legacy-Dienst-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrieren von Diensten legacysprache](../../extensibility/internals/registering-a-legacy-language-service1.md)
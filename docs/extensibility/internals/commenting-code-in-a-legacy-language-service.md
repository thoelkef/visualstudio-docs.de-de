---
title: Kommentieren von Code in einen Legacy-Sprachdienst | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8952612c9502704f79410461d29ca8ab87fa3ee4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Kommentieren von Code in einen Legacy-Sprachdienst
Programmiersprachen bieten in der Regel eine Möglichkeit zum Kommentieren, oder kommentieren Sie den Code. Ein Kommentar ist ein Abschnitt des Texts, die enthält zusätzliche Informationen zu den Code wird jedoch ignoriert, während der Kompilierung oder Interpretation erfordern.  
  
 Die verwaltete Package Framework (MPF) Klassen bieten Unterstützung für Kommentare und uncommenting markierten Text.  
  
## <a name="comment-styles"></a>Comment-Stile  
 Es gibt zwei allgemeine Stile des Kommentars:  
  
1.  Zeile Kommentare, in dem sich der Kommentar in einer einzelnen Zeile befindet.  
  
2.  Block-Kommentare, bei denen der Kommentar mehrere Zeilen enthalten kann.  
  
 Zeile Kommentare haben in der Regel ein (oder Anfangszeichen), während der Block Kommentare Start-und Endzeichen haben. Beispielsweise in c# ist ein Zeilenkommentar beginnt mit / /- und ein Blockkommentar beginnt mit / * und endet mit \*/.  
  
 Wenn der Benutzer den Befehl auswählt **Auswahl kommentieren** aus der **bearbeiten** -> **erweitert** im Menü der Befehl weitergeleitet wird die <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> Methode für die <xref:Microsoft.VisualStudio.Package.Source> Klasse. Wenn der Benutzer den Befehl auswählt **Auswahl kommentieren**, der Befehl weitergeleitet wird, um die <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> Methode.  
  
## <a name="supporting-code-comments"></a>Unterstützung von Kommentaren im Code  
 Können Sie Ihre Kommentare Language Service Unterstützung Code mithilfe von der `EnableCommenting` benannte Parameter von der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Dadurch wird die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> Eigenschaft von der <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse. Weitere Informationen zum Festlegen der Sprache Servicce Funktionen finden Sie unter [registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
 Müssen Sie auch überschreiben die <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> -Methode zur Rückgabe einer <xref:Microsoft.VisualStudio.Package.CommentInfo> Struktur mit den Kommentarzeichen für Ihre Sprache. C#-Stil Zeile Kommentarzeichen werden standardmäßig verwendet.  
  
### <a name="example"></a>Beispiel  
 Hier ist eine beispielimplementierung der <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> Methode.  
  
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
 [Legacy-Dienst-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)
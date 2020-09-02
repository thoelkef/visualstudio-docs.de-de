---
title: Kommentieren von Code in einem Legacy Sprachdienst | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd1405456ca9a6ba00926c82bcc7959ea36d26c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160905"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Kommentieren von Code in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Programmiersprachen bieten in der Regel die Möglichkeit, den Code zu kommentieren oder zu kommentieren. Ein Kommentar ist ein Textabschnitt, der zusätzliche Informationen über den Code bereitstellt, aber während der Kompilierung oder Interpretation ignoriert wird.  
  
 Die MPF-Klassen (Managed Package Framework) unterstützen das kommentieren und auskommentieren von ausgewähltem Text.  
  
## <a name="comment-styles"></a>Kommentar Stile  
 Es gibt zwei allgemeine Arten von Kommentaren:  
  
1. Zeilen Kommentare, bei denen sich der Kommentar in einer einzelnen Zeile befindet.  
  
2. Block Kommentare, in denen der Kommentar möglicherweise mehrere Zeilen enthält.  
  
   Zeilen Kommentare verfügen in der Regel über ein Anfangs Zeichen (oder Zeichen), während Block Kommentare sowohl Start-als auch Endzeichen aufweisen. In c# beginnt beispielsweise ein Zeilenkommentar mit//, und ein Block Kommentar beginnt mit/* und endet mit/ \* .  
  
   Wenn der Benutzer die Befehls **Kommentar Auswahl** im Menü **Bearbeiten**  ->  **erweitert** auswählt, wird der Befehl an die- <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> Methode der- <xref:Microsoft.VisualStudio.Package.Source> Klasse weitergeleitet. Wenn der Benutzer den Befehl **Auskommentierung der Auswahl**auswählt, wird der Befehl an die-Methode weitergeleitet <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> .  
  
## <a name="supporting-code-comments"></a>Unterstützende Code Kommentare  
 Der Sprachdienst kann Code Kommentare mithilfe des `EnableCommenting` benannten Parameters von unterstützen <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Dadurch wird die- <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> Eigenschaft der-Klasse festgelegt <xref:Microsoft.VisualStudio.Package.LanguagePreferences> . Weitere Informationen zum Festlegen von Language servicce-Funktionen finden Sie unter [Registrieren eines Legacy sprach Dienstanbieter](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
 Außerdem müssen Sie die- <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> Methode überschreiben, um eine- <xref:Microsoft.VisualStudio.Package.CommentInfo> Struktur mit den Kommentarzeichen für Ihre Sprache zurückzugeben. Der Standardwert für Zeilenkommentar Zeichen im c#-Stil.  
  
### <a name="example"></a>Beispiel  
 Im folgenden finden Sie eine Beispiel Implementierung der- <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> Methode.  
  
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
 [Funktionen von Legacy Sprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrieren eines Legacysprachdiensts](../../extensibility/internals/registering-a-legacy-language-service1.md)

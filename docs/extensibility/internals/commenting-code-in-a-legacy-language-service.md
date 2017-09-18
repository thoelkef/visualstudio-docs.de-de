---
title: "Kommentieren von Code in einer Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Kommentare, die Unterstützung in Sprachdienste [Verwaltetes Paketframework]"
  - "Sprachdienste [Verwaltetes Paketframework], Kommentare im code"
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Kommentieren von Code in einer Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Programmiersprachen bieten in der Regel besagt, Anmerkungen hinzuzufügen oder Auskommentieren der Code.  Ein Kommentar ist ein Textabschnitt, der zusätzliche Informationen über den Code, sondern wird während der Kompilierung oder der Interpretation ignoriert.  
  
 Die Klassen des verwalteten Paketframeworks \(MPF\) bieten Unterstützung für das Kommentieren und heben Sie die Auskommentierung des ausgewählten Texts.  
  
## Kommentar\-Formate  
 Es gibt zwei allgemeine Format des Kommentars:  
  
1.  Kommentar Kommentare ein, wo der Zeilen in einer einzigen Zeile befindet.  
  
2.  Blockieren von Kommentaren, in denen der Kommentar möglicherweise mehrere Zeilen enthält.  
  
 Zeilen können Kommentare in der Regel ein Anfangszeichen \(oder Zeichen\), während Blocks Kommentare ein Start\- und Endzeichen haben.  Zum Beispiel in C\#, in den Zeilen eines kommentars mit \/\/beginnt und einem Block beginnt mit\/\* kommentars und endet mit \*\/.  
  
 Wenn der Benutzer den Befehl **Auswahl kommentieren** von **Bearbeiten** auswählt \- Menü \> **Erweitert** , der Befehl wird auf die <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A>\-Methode für die <xref:Microsoft.VisualStudio.Package.Source>\-Klasse weitergeleitet.  Wenn der Benutzer den Befehl **Auskommentierung der Auswahl aufheben**auswählt, wird der Befehl zur <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A>\-Methode weitergeleitet.  
  
## Code\-Kommentare unterstützen  
 Sie können die Sprachendienst\-Stütz Code Kommentare mithilfe des `EnableCommenting` benannten Parameters <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> haben.  Hierdurch wird die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A>\-Eigenschaft der <xref:Microsoft.VisualStudio.Package.LanguagePreferences>\-Klasse fest.  Weitere Informationen zum Festlegen servicce Entwicklungssprache Funktionen finden Sie unter [Registriert eine Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service1.md)\).  
  
 Sie müssen die <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>\-Methode überschreiben, um eine <xref:Microsoft.VisualStudio.Package.CommentInfo> Struktur mit den Kommentarzeichen für die Programmiersprache zurückzugeben.  C\#\-Format Zeilen\-Kommentar Zeichen sind die Standardeinstellung.  
  
### Beispiel  
 Im Folgenden finden Sie eine Beispielimplementierung der <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>\-Methode.  
  
```c#  
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
  
## Siehe auch  
 [Legacy\-Dienst\-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registriert eine Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service1.md)
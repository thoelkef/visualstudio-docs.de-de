---
title: Element Vervollständigung in einem Legacy Sprachdienst | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 93182d61b6ecf5bf22ea7117bf8ccfd17e2acd1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841059"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Membervervollständigung in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der IntelliSense-Element Abschluss ist eine QuickInfo, die eine Liste möglicher Member eines bestimmten Bereichs, z. b. eine Klasse, Struktur, Enumeration oder einen Namespace, anzeigt. Wenn beispielsweise der Benutzer in c# "This" gefolgt von einem bestimmten Zeitraum eingibt, wird eine Liste aller Member der Klasse oder Struktur im aktuellen Bereich in einer Liste angezeigt, aus der der Benutzer auswählen kann.  
  
 Das Managed Package Framework (MPF) bietet Unterstützung für die QuickInfo und die Verwaltung der Liste in der QuickInfo. alles, was benötigt wird, ist die Zusammenarbeit des Parsers, um die in der Liste angezeigten Daten bereitzustellen.  
  
 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen finden Sie unter [Erweitern des Editors und der Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.  
  
## <a name="how-it-works"></a>Funktionsweise  
 Im folgenden finden Sie zwei Möglichkeiten, wie eine Elementliste mit den MPF-Klassen angezeigt wird:  
  
- Positionieren der Einfügemarke für einen Bezeichner oder nach einem Element Abschluss Zeichen und Auswählen von Member **auflisten** aus dem **IntelliSense** -Menü.  
  
- Der <xref:Microsoft.VisualStudio.Package.IScanner> Scanner erkennt ein Element Abschluss Zeichen und legt einen <xref:Microsoft.VisualStudio.Package.TokenTriggers> tokenauslösers von für dieses Zeichen fest.  
  
  Ein Element Abschluss Zeichen gibt an, dass ein Member einer Klasse, Struktur oder Enumeration befolgt werden soll. Beispielsweise ist in c# oder Visual Basic das Element Abschluss Zeichen ein `.` , während in C++ das Zeichen entweder ein `.` oder ein ist `->` . Der Wert des Auslösers wird festgelegt, wenn das Element Select-Zeichen gescannt wird.  
  
### <a name="the-intellisense-member-list-command"></a>Der IntelliSense-Member List-Befehl  
 Der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> -Befehl initiiert einen Aufruf der <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> -Methode für die <xref:Microsoft.VisualStudio.Package.Source> -Klasse, und die- <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode ruft wiederum den <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methoden Parser mit der analysieren-Ursache von auf <xref:Microsoft.VisualStudio.Package.ParseReason> .  
  
 Der Parser bestimmt sowohl den Kontext der aktuellen Position als auch das Token unter oder unmittelbar vor der aktuellen Position. Basierend auf diesem Token wird eine Liste von Deklarationen angezeigt. Wenn Sie in c# z. b. die Einfügemarke für einen Klassenmember positionieren und Member **auflisten**auswählen, erhalten Sie eine Liste aller Member der Klasse. Wenn Sie die Einfügemarke nach einem Punkt positionieren, der auf eine Objekt Variable folgt, erhalten Sie eine Liste aller Member der Klasse, die das Objekt darstellt. Beachten Sie Folgendes: Wenn die Einfügemarke auf einem Element positioniert ist, wenn die Elementliste angezeigt wird, wird durch die Auswahl eines Elements aus der Liste der Member, auf dem sich die Einfügemarke befindet, durch den in der Liste angezeigten  
  
### <a name="the-token-trigger"></a>Der tokenauslöse  
 Der <xref:Microsoft.VisualStudio.Package.TokenTriggers> -Triggern initiiert einen Aufruf der <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> -Methode für die <xref:Microsoft.VisualStudio.Package.Source> -Klasse, und die- <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode ruft wiederum den Parser mit der analysieren-Ursache von auf <xref:Microsoft.VisualStudio.Package.ParseReason> (wenn der tokentriggern auch das- <xref:Microsoft.VisualStudio.Package.TokenTriggers> Flag enthielt, ist die analysieren-Ursache, die Element <xref:Microsoft.VisualStudio.Package.ParseReason> Auswahl und geschweifter Klammer hervorheben).  
  
 Der Parser bestimmt sowohl den Kontext der aktuellen Position als auch das, was vor dem Element Select-Zeichen eingegeben wurde. Aus diesen Informationen erstellt der Parser eine Liste aller Member des angeforderten Bereichs. Diese Liste von Deklarationen wird im- <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt gespeichert, das von der-Methode zurückgegeben wird <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> . Wenn eine Deklaration zurückgegeben wird, wird die QuickInfo für den Abschluss des Elements angezeigt. Die QuickInfo wird von einer Instanz der- <xref:Microsoft.VisualStudio.Package.CompletionSet> Klasse verwaltet.  
  
## <a name="enabling-support-for-member-completion"></a>Aktivieren der Unterstützung für die Beendigung von  
 Der `CodeSense` Registrierungs Eintrag muss auf 1 festgelegt sein, um einen beliebigen IntelliSense-Vorgang zu unterstützen. Dieser Registrierungs Eintrag kann mit einem benannten Parameter festgelegt werden, der an das Benutzer Attribut übergeben wurde, <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> das dem Sprachpaket zugeordnet ist. Die Sprachdienst Klassen lesen den Wert dieses Registrierungs Eintrags aus der-Eigenschaft der- <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse.  
  
 Wenn der Scanner den tokenfehler zurückgibt <xref:Microsoft.VisualStudio.Package.TokenTriggers> und der Parser eine Liste von Deklarationen zurückgibt, wird die Element Vervollständigungsliste angezeigt.  
  
## <a name="supporting-member-completion-in-the-scanner"></a>Unterstützen der Vervollständigung von Membern im Scanner  
 Der Scanner muss in der Lage sein, ein Element Abschluss Zeichen zu erkennen und den tokenauslösers von festzulegen <xref:Microsoft.VisualStudio.Package.TokenTriggers> , wenn dieses Zeichen analysiert wird.  
  
### <a name="example"></a>Beispiel  
 Hier ist ein vereinfachtes Beispiel für das Erkennen des Element Abschluss Zeichens und das Festlegen des entsprechenden <xref:Microsoft.VisualStudio.Package.TokenTriggers> Flags angegeben. Dieses Beispiel dient nur zu Illustrations Zwecken. Dabei wird davon ausgegangen, dass der Scanner eine Methode enthält `GetNextToken` , die Token aus einer Textzeile identifiziert und zurückgibt. Der Beispielcode legt einfach den-Wert fest, wenn er die richtige Art von Zeichen sieht.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char memberSelectChar = '.';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (c == memberSelectChar)  
                {  
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;  
                }  
            }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-member-completion-in-the-parser"></a>Unterstützen der Element Vervollständigung im Parser  
 Bei der Beendigung des Elements <xref:Microsoft.VisualStudio.Package.Source> Ruft die-Klasse die- <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> Methode auf. Sie müssen die Liste in einer Klasse implementieren, die von der- <xref:Microsoft.VisualStudio.Package.Declarations> Klasse abgeleitet wird. Weitere <xref:Microsoft.VisualStudio.Package.Declarations> Informationen zu den Methoden, die Sie implementieren müssen, finden Sie in der-Klasse.  
  
 Der Parser wird mit oder aufgerufen, <xref:Microsoft.VisualStudio.Package.ParseReason> <xref:Microsoft.VisualStudio.Package.ParseReason> Wenn ein Member Select-Zeichen eingegeben wird. Der im-Objekt angegebene Speicherort <xref:Microsoft.VisualStudio.Package.ParseRequest> ist unmittelbar nach dem Element Select-Zeichen. Der Parser muss die Namen aller Member erfassen, die an dieser Stelle im Quellcode in einer Elementliste vorkommen können. Der Parser muss dann die aktuelle Zeile analysieren, um den Bereich zu bestimmen, den der Benutzer dem Element Select-Zeichen zugeordnet werden soll.  
  
 Dieser Bereich basiert auf dem Bezeichnertyp vor dem Element Select-Zeichen. Wenn z. b. in c# die Member-Variable mit dem `languageService` Typ ist `LanguageService` , wird **LanguageService eingegeben.** erzeugt eine Liste aller Member der- `LanguageService` Klasse. Geben Sie auch in c# ein **.** erzeugt eine Liste aller Member der-Klasse im aktuellen Bereich.  
  
### <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Möglichkeit, eine <xref:Microsoft.VisualStudio.Package.Declarations> Liste aufzufüllen. In diesem Code wird davon ausgegangen, dass der Parser eine Deklaration erstellt und Sie der Liste hinzufügt, indem eine- `AddDeclaration` Methode für die-Klasse aufgerufen wird `TestAuthoringScope` .  
  
```csharp  
using System.Collections;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    internal class TestDeclaration  
    {  
        public string Name;            // Name of declaration  
        public int     TypeImageIndex; // Glyph index  
        public string Description;     // Description of declaration  
  
        public TestDeclaration(string name, int typeImageIndex, string description)  
        {  
            this.Name = name;  
            this.TypeImageIndex = typeImageIndex;  
            this.Description = description;  
        }  
    }  
  
    //===================================================  
    internal class TestDeclarations : Declarations  
    {  
        private ArrayList declarations;  
  
        public TestDeclarations()  
            : base()  
        {  
            declarations = new ArrayList();  
        }  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            declarations.Add(declaration);  
        }  
  
        //////////////////////////////////////////////////////////////////////  
        // Declarations of class methods that must be implemented.  
        public override int GetCount()  
        {  
            // Return the number of declarations to show.  
            return declarations.Count;  
        }  
  
        public override string GetDescription(int index)  
        {  
            // Return the description of the specified item.  
            string description = "";  
            if (index >= 0 && index < declarations.Count)  
            {  
                description = ((TestDeclaration)declarations[index]).Description;  
            }  
            return description;  
        }  
  
        public override string GetDisplayText(int index)  
        {  
            // Determine what is displayed in the tool tip list.  
            string text = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                text = ((TestDeclaration)declarations[index]).Name;  
            }  
            return text;  
        }  
  
        public override int GetGlyph(int index)  
        {  
            // Return index of image to display next to the display text.  
            int imageIndex = -1;  
            if (index >= 0 && index < declarations.Count)  
            {  
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;  
            }  
            return imageIndex;  
        }  
  
        public override string GetName(int index)  
        {  
            string name = null;  
            if (index >= 0 && index < declarations.Count)  
            {  
                name = ((TestDeclaration)declarations[index]).Name;  
            }  
            return name;  
        }  
    }  
  
    //===================================================  
    public class TestAuthoringScope : AuthoringScope  
    {  
        private TestDeclarations declarationsList;  
  
        public void AddDeclaration(TestDeclaration declaration)  
        {  
            if (declaration != null)  
            {  
                if (declarationsList == null)  
                {  
                    declarationsList = new TestDeclarations();  
                }  
                declarationsList.AddDeclaration(declaration);  
            }  
        }  
  
        public override Declarations GetDeclarations(IVsTextView view,  
                                                     int line,  
                                                     int col,  
                                                     TokenInfo info,  
                                                     ParseReason reason)  
        {  
            return declarationsList;  
        }  
  
        /////////////////////////////////////////////////  
        // Remainder of AuthoringScope methods not shown.  
        /////////////////////////////////////////////////  
    }  
  
    //===================================================  
    class TestLanguageService : LanguageService  
    {  
        public override AuthoringScope ParseSource(ParseRequest req)  
        {  
            TestAuthoringScope scope = new TestAuthoringScope();  
            if (req.Reason == ParseReason.MemberSelect ||  
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)  
            {  
                // Gather list of declarations based on what the user  
                // has typed so far. In this example, this list is an array of  
                // MemberDeclaration objects (a helper class you might implement  
                // to hold member declarations).  
                // How this list is gathered is dependent on the parser  
                // and is not shown here.  
                MemberDeclarations memberDeclarations;  
                memberDeclarations = GetDeclarationsForScope();  
  
                // Now populate the Declarations list in the authoring scope.  
                // GetImageIndexBasedOnType() is a helper method you  
                // might implement to convert a member type to an index into  
                // the image list returned from the language service.  
                foreach (MemberDeclaration dec in memberDeclarations)  
                {  
                    scope.AddDeclaration(new TestDeclaration(  
                                             dec.Name,  
                                             GetImageIndexBasedOnType(dec.Type),  
                                             dec.Description));  
                }  
            }  
            return scope;  
        }  
    }  
}  
```

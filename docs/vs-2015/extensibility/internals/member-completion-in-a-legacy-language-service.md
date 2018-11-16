---
title: Membervervollständigung in einem Legacysprachdienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b8b5940e473c639600c30e66e7dc0c732359322d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790985"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Membervervollständigung in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der Member IntelliSense-Vervollständigung wird eine QuickInfo, die eine Liste der möglichen Elemente eines bestimmten Bereichs wie z. B. eine Klasse, Struktur, Enumeration oder Namespace angezeigt. Z. B. in C# geschrieben, wenn der Benutzer, "this eingibt" gefolgt von einem Punkt, eine Liste aller Member der Klasse oder Struktur im aktuellen Bereich in einer Liste erhält in dem der Benutzer auswählen kann.  
  
 Das managed Package Framework (MPF) bietet Unterstützung für die QuickInfo und Verwalten der Liste in der QuickInfo. erforderlich ist lediglich die Zusammenarbeit des Parsers, um die Daten anzugeben, die in der Liste angezeigt wird.  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Erweitern des Editors und Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="how-it-works"></a>So funktioniert es  
 Es folgen die beiden Möglichkeiten, die mit die MPF-Klassen, in denen eine Memberliste angezeigt wird:  
  
- Positionieren die Einfügemarke in einem Bezeichner oder nach der ein Vervollständigungszeichen Member und Auswählen von **Listenmember** aus der **IntelliSense** Menü.  
  
- Die <xref:Microsoft.VisualStudio.Package.IScanner> Scanner erkennt ein Vervollständigungszeichen Element und legt einen token Trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> für dieses Zeichen.  
  
  Ein Vervollständigungszeichen Member gibt an, dass ein Mitglied aus einer Klasse, Struktur oder eines Enumerationswerts folgen. In c# oder Visual Basic ist der Member Vervollständigungszeichen z. B. eine `.`, während in C++ das Zeichen entweder eine `.` oder `->`. Der Triggerwert wird festgelegt, wenn das Element auf Zeichen überprüft wird.  
  
### <a name="the-intellisense-member-list-command"></a>Der IntelliSense-Member-List-Befehl  
 Die <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Befehl initiiert einen Aufruf der <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode für die <xref:Microsoft.VisualStudio.Package.Source> Klasse und die <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode wiederum ruft die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode-Parser, mit der Analyse Grund des <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 Der Parser bestimmt den Kontext der aktuellen Position als auch für das Token unter oder unmittelbar vor der aktuellen Position. Auf der Grundlage dieses Tokens, wird eine Liste der Deklarationen angezeigt. Zum Beispiel in C# geschrieben, wenn Sie die position der Einfügemarke auf einen Member der Klasse, und wählen **Listenmember**, erhalten Sie eine Liste aller Member der Klasse. Wenn Sie die Einfügemarke nach einem bestimmten Zeitraum zu, die eine Objektvariable folgt positionieren, erhalten Sie eine Liste aller Member der Klasse das Objekt darstellt. Beachten Sie, wenn die Einfügemarke für ein Element positioniert ist, wenn die Memberliste angezeigt wird, wählen ein Element aus der Liste der Member ersetzt, die, den sich die Einfügemarke zusammen mit einem in der Liste befindet.  
  
### <a name="the-token-trigger"></a>Der Token-Trigger  
 Der <xref:Microsoft.VisualStudio.Package.TokenTriggers> Trigger initiiert einen Aufruf der <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode für die <xref:Microsoft.VisualStudio.Package.Source> Klasse und die <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode wiederum ruft den Parser mit dem Grund Analyse der <xref:Microsoft.VisualStudio.Package.ParseReason> (, wenn der token Trigger, auch enthalten der <xref:Microsoft.VisualStudio.Package.TokenTriggers> Flag Der Grund für die Analyse ist <xref:Microsoft.VisualStudio.Package.ParseReason> kombiniert Member-Auswahl und geschweifte Klammer hervorheben).  
  
 Der Parser bestimmt den Kontext der aktuellen position als auch was bevor das Element auswählen Zeichen eingegeben wurde. Aus diesen Informationen erstellt der Parser eine Liste aller Member, der den angeforderten Bereich. Diese Liste mit Deklarationen befindet sich in der <xref:Microsoft.VisualStudio.Package.AuthoringScope> von zurückgegebene Objekt der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode. Wenn alle Deklarationen zurückgegeben werden, wird die Member-Abschluss-QuickInfo angezeigt. Die QuickInfo wird von einer Instanz verwaltet die <xref:Microsoft.VisualStudio.Package.CompletionSet> Klasse.  
  
## <a name="enabling-support-for-member-completion"></a>Aktivieren der Unterstützung für Membervervollständigung  
 Sie benötigen die `CodeSense` Registrierungseintrags auf 1 festgelegt werden, um ein IntelliSense-Vorgang zu unterstützen. Dieser Registrierungseintrag kann festgelegt werden, mit einem benannten Parameter, die an die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Benutzerattribut das Language Pack zugeordnet. Die Language-Dienstklassen liest den Wert dieses Registrierungseintrags aus der <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Eigenschaft für die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse.  
  
 Wenn der Scanner den token Trigger vom zurückgibt <xref:Microsoft.VisualStudio.Package.TokenTriggers>, ein Parser gibt eine Liste der Deklarationen, und die Member-Vervollständigungsliste angezeigt wird.  
  
## <a name="supporting-member-completion-in-the-scanner"></a>Membervervollständigung unterstützen in der Scanner  
 Die Überprüfung muss erkennen ein Vervollständigungszeichen Member, und legen Sie den token Trigger von <xref:Microsoft.VisualStudio.Package.TokenTriggers> Wenn dieses Zeichen wird analysiert.  
  
### <a name="example"></a>Beispiel  
 Hier ist ein vereinfachtes Beispiel Erkennen von der Members-Vervollständigungszeichen und zum Festlegen der entsprechenden <xref:Microsoft.VisualStudio.Package.TokenTriggers> Flag. In diesem Beispiel ist nur zur Veranschaulichung. Es wird davon ausgegangen, dass Ihre Überprüfung eine Methode enthält `GetNextToken` identifiziert und gibt die Token von einer Textzeile zurück. Der Beispielcode legt den Trigger einfach, wenn es erkennt, dass die richtige Art von Zeichen.  
  
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
  
## <a name="supporting-member-completion-in-the-parser"></a>Membervervollständigung unterstützt in der Parser  
 Für den Abschluss der Member die <xref:Microsoft.VisualStudio.Package.Source> -Klasse ruft die <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> Methode. Sie müssen die Liste implementieren, in eine abgeleitete Klasse, aus der <xref:Microsoft.VisualStudio.Package.Declarations> Klasse. Finden Sie unter den <xref:Microsoft.VisualStudio.Package.Declarations> -Klasse Weitere Informationen zu den Methoden, die Sie implementieren müssen.  
  
 Der Parser aufgerufen wird und <xref:Microsoft.VisualStudio.Package.ParseReason> oder <xref:Microsoft.VisualStudio.Package.ParseReason> Wenn ein Element auf Zeichen eingegeben wird. Den Speicherort, der <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt ist, sofort, nachdem das Element ausgewählt haben Zeichen. Der Parser muss die Namen aller Elemente erfasst werden, die in einer Memberliste zum jeweiligen Zeitpunkt im Quellcode angezeigt werden können. Klicken Sie dann analysiert der Parser die aktuelle Zeile aus, um den Bereich zu ermitteln, die, den der Benutzer das Element auf Zeichen zugeordnet möchte.  
  
 Dieser Bereich basiert auf den Typ des Bezeichners, bevor das Element auswählen Zeichen. In C# geschrieben, betrachten Sie die Membervariable `languageService` aufweist eine Art von `LanguageService`eingeben **LanguageService.** erstellt eine Liste aller Member der `LanguageService` Klasse. Auch in c# eingeben **dies.** erstellt eine Liste aller Member der Klasse im aktuellen Bereich.  
  
### <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Möglichkeit zum Auffüllen einer <xref:Microsoft.VisualStudio.Package.Declarations> Liste. Dieser Code setzt voraus, dass der Parser eine Deklaration erstellt und fügt es der Liste hinzu, durch den Aufruf einer `AddDeclaration` Methode für die `TestAuthoringScope` Klasse.  
  
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


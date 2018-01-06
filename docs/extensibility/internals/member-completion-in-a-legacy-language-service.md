---
title: Member-Abschluss in einen Legacy-Sprachdienst | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e77511bdaaa96dc75f5be75c175b63fcd3cc3253
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="member-completion-in-a-legacy-language-service"></a>Member-Abschluss in einen Legacy-Sprachdienst
Die IntelliSense-Anweisungsvervollständigung Mitglied wird eine QuickInfo, die zeigt eine Liste der möglichen Elemente eines bestimmten Bereichs z. B. eine Klasse, Struktur, Enumeration oder Namespace an. Beispielsweise in C# geschrieben, wenn der Benutzer, "this eingibt" gefolgt von einem Punkt eine Liste aller Member der Klasse oder Struktur im aktuellen Bereich in einer Liste erhält in dem der Benutzer auswählen kann.  
  
 Des managed Package Framework (MPF) bietet Unterstützung für die QuickInfo und die Verwaltung der Liste in der QuickInfo an. benötigtes lediglich Zusammenarbeit vom Parser die Daten angeben, die in der Liste angezeigt wird.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Erweiterung des Editors und des Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="how-it-works"></a>Funktionsweise  
 Im folgenden sind die zwei Möglichkeiten, mit die MPF-Klassen, in denen eine Memberliste angezeigt wird:  
  
-   Positionieren die Einfügemarke auf einen Bezeichner oder ein Member Abschluss Strich und auswählen **Listenmember** aus der **IntelliSense** Menü.  
  
-   Die <xref:Microsoft.VisualStudio.Package.IScanner> Scanner eine Member-Abschluss-Zeichen erkennt und legt einen token Trigger des <xref:Microsoft.VisualStudio.Package.TokenTriggers> für dieses Zeichen.  
  
 Ein Member Abschluss Zeichen gibt an, dass ein Mitglied aus einer Klasse, Struktur oder Enumeration folgen. In c# oder Visual Basic ist das Element Abschluss Zeichen z. B. eine `.`, während in C++ die Zeichen entweder eine `.` oder ein `->`. Der Triggerwert wird festgelegt, wenn das Element select Zeichen überprüft wird.  
  
### <a name="the-intellisense-member-list-command"></a>Der IntelliSense-Member-List-Befehl  
 Die <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Befehl startet einen Aufruf der <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode auf die <xref:Microsoft.VisualStudio.Package.Source> Klasse und die <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode wiederum die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode Parser mit dem Grund der Analyse von <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 Der Parser bestimmt den Kontext der aktuellen Position als auch das Token unter oder unmittelbar vor der aktuellen Position. Anhand dieses Token, erhält eine Liste der Deklarationen. Beispielsweise in C# geschrieben, wenn Sie die position der Einfügemarke auf einen Klassenmember, und wählen **Listenmember**, erhalten Sie eine Liste aller Member der Klasse. Wenn die position der Einfügemarke nach einem bestimmten Zeitraum, die eine Objektvariable folgt, erhalten Sie eine Liste aller Member der Klasse das Objekt darstellt. Beachten Sie, dass, wenn die Einfügemarke für ein Element positioniert ist, wenn die Memberliste angezeigt wird, wählen ein Element aus der Liste der Member ersetzt, auf das Caretzeichen mit einem in der Liste aus.  
  
### <a name="the-token-trigger"></a>Die Token-Trigger  
 Der <xref:Microsoft.VisualStudio.Package.TokenTriggers> Trigger initiiert, einen Aufruf von der <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode auf der <xref:Microsoft.VisualStudio.Package.Source> Klasse und die <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode wiederum ruft den Parser mit dem Grund der Analyse von <xref:Microsoft.VisualStudio.Package.ParseReason> (wenn auch der token Trigger enthalten die <xref:Microsoft.VisualStudio.Package.TokenTriggers> Flag Der Grund für die Analyse ist <xref:Microsoft.VisualStudio.Package.ParseReason> Memberauswahl und geschweifte Klammer hervorheben kombiniert).  
  
 Der Parser bestimmt den Kontext der aktuellen position sowie was vor das Element auswählen, Zeichen eingegeben wurde. Aus diesen Informationen erstellt eine Liste aller Member im angeforderten Bereich. Diese Liste der Deklarationen wird gespeichert, der <xref:Microsoft.VisualStudio.Package.AuthoringScope> von zurückgegebene Objekt der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode. Wenn alle Deklarationen zurückgegeben werden, wird die Member-Abschluss-QuickInfo angezeigt. Die QuickInfo wird von einer Instanz von verwaltet die <xref:Microsoft.VisualStudio.Package.CompletionSet> Klasse.  
  
## <a name="enabling-support-for-member-completion"></a>Aktivieren der Unterstützung für Member Abschluss  
 Sie benötigen die `CodeSense` Registrierungseintrag auf 1 festgelegt werden, um alle IntelliSense-Vorgangs zu unterstützen. Dieses Registrierungseintrags kann festgelegt werden, mit einem benannten Parameter übergeben, um die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Benutzerattribut, die die deutschsprachige Paket zugeordnet. Die Language-Dienstklassen lesen Sie den Wert dieses Registrierungseintrags aus der <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Eigenschaft auf die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse.  
  
 Wenn der Scanner den token Auslöser des zurückgibt <xref:Microsoft.VisualStudio.Package.TokenTriggers>, und der Parser gibt eine Liste der Deklarationen, wird die Vervollständigungsliste Member angezeigt.  
  
## <a name="supporting-member-completion-in-the-scanner"></a>Member-Abschluss unterstützen in der Scanner  
 Der Scanner muss in der Lage, ein Member Abschluss Zeichen zu erkennen, und legen Sie den token Auslöser des <xref:Microsoft.VisualStudio.Package.TokenTriggers> Wenn dieses Zeichen wird analysiert.  
  
### <a name="example"></a>Beispiel  
 Hier ist ein vereinfachtes Beispiel erkennen das Element Abschluss Zeichen und Festlegen der entsprechenden <xref:Microsoft.VisualStudio.Package.TokenTriggers> Flag. In diesem Beispiel wird nur zur Veranschaulichung. Es wird davon ausgegangen, dass der Scanner eine Methode enthält `GetNextToken` , kennzeichnet, und gibt die Token aus einer Zeile des Texts zurück. Der Beispielcode legt den Trigger einfach fest, wenn es erkennt, dass die richtige Art von Zeichen.  
  
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
  
## <a name="supporting-member-completion-in-the-parser"></a>Unterstützen von Member-Abschluss in der Parser  
 Auf den Abschluss der Member die <xref:Microsoft.VisualStudio.Package.Source> -Klasse ruft die <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> Methode. Sie müssen die Liste implementieren, in einer Klasse, die abgeleitet ist die <xref:Microsoft.VisualStudio.Package.Declarations> Klasse. Finden Sie unter der <xref:Microsoft.VisualStudio.Package.Declarations> Klasse ausführliche Informationen über die Methoden, die Sie implementieren müssen.  
  
 Der Parser aufgerufen wird, und <xref:Microsoft.VisualStudio.Package.ParseReason> oder <xref:Microsoft.VisualStudio.Package.ParseReason> Wenn ein Element auswählen Zeichen typisiert ist. Die im angegebenen Speicherort der <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt ist, sofort, nachdem das Element ausgewählt Zeichen. Der Parser muss die Namen aller Elemente erfassen, die in einer Memberliste an dieser bestimmten Stelle im Quellcode angezeigt werden können. Klicken Sie dann analysiert der Parser die aktuelle Zeile aus, um den Umfang zu bestimmen, den der Benutzer das Element select Zeichen zugeordnet möchte.  
  
 Dieser Bereich basiert auf den Typ des Bezeichners, bevor das Element auswählen Zeichen. Beispielsweise in C# geschrieben, erhält die Membervariable `languageService` , besitzt einen Typ von `LanguageService`, geben **LanguageService.** erzeugt eine Liste aller Member der `LanguageService` Klasse. Auch in c# eingeben **dies.** erstellt eine Liste aller Member der Klasse im aktuellen Bereich.  
  
### <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Möglichkeit zum Auffüllen einer <xref:Microsoft.VisualStudio.Package.Declarations> Liste. Mit diesem Code wird davon ausgegangen, dass der Parser eine Deklaration erstellt, und es der Liste durch Aufrufen Fügt einer `AddDeclaration` Methode für die `TestAuthoringScope` Klasse.  
  
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
---
title: "Member-Abschluss in einer Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense, QuickInfo Member Abschluss"
  - "Member-Abschluss, Unterstützung in Sprachdienste [Verwaltetes Paketframework]"
  - "Sprachdienste [Verwaltetes Paketframework], IntelliSense-Member-Vervollständigung"
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Member-Abschluss in einer Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die IntelliSense\-Vervollständigung Member ist eine QuickInfo, die eine Liste der möglichen Elemente eines bestimmten Bereichs wie z. B. eine Klasse, Struktur, Enumeration oder Namespace angezeigt. Z. B. in c\#, wird Wenn der Benutzer "this gibt" gefolgt von einem Punkt, eine Liste aller Member der Klasse oder Struktur im aktuellen Bereich in einer Liste angezeigt aus der der Benutzer auswählen kann.  
  
 Das verwaltete Package Framework \(MPF\) bietet Unterstützung für die QuickInfo und die Verwaltung der Liste in der QuickInfo. erforderlich ist, ist die Zusammenarbeit vom Parser zum Bereitstellen der Daten, die in der Liste angezeigt wird.  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Um weitere Informationen finden Sie unter [Erweitern der\-Editor und Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
## So funktioniert es  
 Folgendes sind die beiden Methoden in denen Elementliste angezeigt wird mithilfe der MPF\-Klassen:  
  
-   Positionieren die Einfügemarke auf einen Bezeichner oder nach einem Element Abschluss\-Zeichen und auswählen **Mitglieder** aus der **IntelliSense** Menü.  
  
-   Die <xref:Microsoft.VisualStudio.Package.IScanner> Scanner erkennt ein Member Abschluss Zeichen und legt einen token Trigger des <xref:Microsoft.VisualStudio.Package.TokenTriggers> für das jeweilige Zeichen.  
  
 Ein Member Abschluss Zeichen gibt an, dass ein Member der Klasse, Struktur oder Enumeration folgen. In c\# oder Visual Basic ist das Element Abschluss Zeichen z. B. ein `.`, während in C\+\+ das Zeichen entweder ein `.` oder ein `->`. Der Triggerwert wird festgelegt, wenn das Element wählen Zeichen überprüft wird.  
  
### Der IntelliSense\-Member\-List\-Befehl  
 Die <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Befehl initiiert einen Aufruf der <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode für die <xref:Microsoft.VisualStudio.Package.Source> Klasse und die <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode wiederum ruft die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode Parser mit dem Grund Analyse der <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 Der Parser bestimmt den Kontext der aktuellen Position als auch das Token unter oder unmittelbar vor der aktuellen Position. Anhand dieses Token, wird eine Liste der Deklarationen angezeigt. Wenn beispielsweise in c\#, wenn Sie die position der Einfügemarke auf einen Member der Klasse, und wählen **Mitglieder**, erhalten Sie eine Liste aller Member der Klasse. Wenn Sie die Einfügemarke nach einem bestimmten Zeitraum, die eine Objektvariable folgt positionieren, erhalten Sie eine Liste aller Member der Klasse das Objekt darstellt. Beachten Sie, wenn die Einfügemarke für ein Element positioniert ist, wenn die Memberliste angezeigt wird, ein Element aus der Liste auswählen das Element ersetzt werden, das die Einfügemarke durch die in der Liste befindet.  
  
### Der Token\-Trigger  
 Die <xref:Microsoft.VisualStudio.Package.TokenTriggers> Trigger initiiert einen Aufruf der <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode auf die <xref:Microsoft.VisualStudio.Package.Source> Klasse und die <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Methode wiederum ruft den Parser mit der Analyse Ursache des <xref:Microsoft.VisualStudio.Package.ParseReason> \(wenn auch der token Trigger enthalten die <xref:Microsoft.VisualStudio.Package.TokenTriggers> Flag der Grund für die Analyse ist <xref:Microsoft.VisualStudio.Package.ParseReason> kombiniert Elementauswahl und geschweifte Klammer hervorheben\).  
  
 Der Parser bestimmt den Kontext der aktuellen position als auch was vor dem Auswählen des Members Zeichen eingegeben wurde. Aus diesen Informationen erstellt der Parser eine Liste aller Mitglieder der angeforderte Bereich. Diese Liste der Deklarationen wird gespeichert, der <xref:Microsoft.VisualStudio.Package.AuthoringScope> \-Objekt, das zurückgegeben wird von der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode. Wenn alle Deklarationen zurückgegeben werden, wird der Member Abschluss\-QuickInfo angezeigt. Die QuickInfo wird von einer Instanz verwaltet die <xref:Microsoft.VisualStudio.Package.CompletionSet> Klasse.  
  
## Aktivieren der Unterstützung für Member Abschluss  
 Sie müssen die `CodeSense` Registrierungseintrag auf 1 festgelegt werden, um alle IntelliSense\-Vorgang zu unterstützen. Dieser Registrierungseintrag kann festgelegt werden, mit einem benannten Parameter zu übergeben der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Benutzerattribut das Sprachpaket zugeordnet. Die Dienstklassen Sprache lesen den Wert dieses Registrierungseintrags aus der <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> \-Eigenschaft für die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse.  
  
 Wenn der Scanner den token Trigger gibt <xref:Microsoft.VisualStudio.Package.TokenTriggers>, ein Parser gibt eine Liste der Deklarationen, und die Member\-Vervollständigungsliste wird angezeigt.  
  
## Member\-Abschluss unterstützen im Scanner  
 Der Scanner muss ein Member Abschluss Zeichen zu erkennen, und legen Sie den token Trigger können <xref:Microsoft.VisualStudio.Package.TokenTriggers> Wenn dieses Zeichen wird analysiert.  
  
### Beispiel  
 Hier ist ein vereinfachtes Beispiel erkennen das Element Abschluss Zeichen und Festlegen der entsprechenden <xref:Microsoft.VisualStudio.Package.TokenTriggers> Flag. In diesem Beispiel wird nur zur Veranschaulichung. Es wird davon ausgegangen, dass der Scanner eine Methode enthält `GetNextToken` identifiziert wird und gibt die Token aus einer Textzeile zurück. Im Beispielcode wird einfach den Trigger, wenn es erkennt, dass die richtige Art von Zeichen.  
  
```c#  
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
  
## Member\-Abschluss unterstützt im Parser  
 Für den Abschluss der Member die <xref:Microsoft.VisualStudio.Package.Source> \-Klasse ruft die <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> Methode. Sie müssen die Liste in einer Klasse, die von abgeleitet ist implementieren die <xref:Microsoft.VisualStudio.Package.Declarations> Klasse. Finden Sie unter der <xref:Microsoft.VisualStudio.Package.Declarations> \-Klasse zu den Methoden, die Sie implementieren müssen.  
  
 Der Parser aufgerufen wird und <xref:Microsoft.VisualStudio.Package.ParseReason> oder <xref:Microsoft.VisualStudio.Package.ParseReason> Wenn ein Element wählen Zeichen eingegeben wird. Der Speicherort der <xref:Microsoft.VisualStudio.Package.ParseRequest> \-Objekt ist, sobald das Element wählen Sie Zeichen aus. Der Parser muss die Namen aller Elemente sammeln, die in der einen bestimmten Zeitpunkt im Quellcode angezeigt werden können. Klicken Sie dann analysiert der Parser die aktuelle Zeile aus, um festzulegen, die der Benutzer das Element wählen Zeichen zugeordnet haben möchte.  
  
 Dieser Bereich basiert auf den Typ des Bezeichners, bevor das Element auswählen Zeichen. In c\#, betrachten Sie die Membervariable `languageService` bei dem ein `LanguageService`, eingeben **LanguageService.** erzeugt eine Liste aller Member der `LanguageService` Klasse. Auch in c\# eingeben **dies.** erzeugt eine Liste aller Member der Klasse im aktuellen Bereich.  
  
### Beispiel  
 Das folgende Beispiel zeigt eine Möglichkeit zum Auffüllen einer <xref:Microsoft.VisualStudio.Package.Declarations> Liste. Dieser Code setzt voraus, dass der Parser eine Deklaration erstellt und durch Aufrufen der Liste hinzugefügt eine `AddDeclaration` Methode für die `TestAuthoringScope` Klasse.  
  
```c#  
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
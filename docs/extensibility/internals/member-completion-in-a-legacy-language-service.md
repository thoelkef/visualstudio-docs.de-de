---
title: Abschluss von Mitgliedern in einem Legacy-Sprachdienst | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6445aec4954590e4d361189f053592eebe7767e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707195"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Membervervollständigung in einem Legacysprachdienst

Die IntelliSense-Membervervollständigung ist ein QuickInfo, der eine Liste möglicher Member eines bestimmten Bereichs anzeigt, z. B. eine Klasse, Struktur, Enumeration oder einen Namespace. Wenn der Benutzer z. B. "this" gefolgt von einem Punkt eingibt, wird in einer Liste, aus der der Benutzer auswählen kann, eine Liste aller Member der Klasse oder Struktur im aktuellen Bereich angezeigt.

Das Managed Package Framework (MPF) bietet Unterstützung für die QuickInfo und die Verwaltung der Liste in der Tooltip. Alles, was benötigt wird, ist die Zusammenarbeit des Parsers, um die in der Liste angezeigten Daten zur Verfügung zu stellen.

Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen finden Sie unter [Erweitern des Editors und der Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

## <a name="how-it-works"></a>Funktionsweise

Im Folgenden sind die beiden Möglichkeiten aufgeführt, wie eine Mitgliederliste mithilfe der MPF-Klassen angezeigt wird:

- Positionieren der Einsparung auf einem Bezeichner oder nach einem Elementabschlusszeichen und Auswählen von **Listenmitgliedern** im **Menü IntelliSense.**

- Der <xref:Microsoft.VisualStudio.Package.IScanner> Scanner erkennt ein Elementabschlusszeichen und legt einen Token-Trigger von [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) für dieses Zeichen fest.

Ein Memberabschlusszeichen gibt an, dass ein Member einer Klasse, Struktur oder Enumeration folgen soll. In C- oder Visual Basic ist z. `.`B. das Elementabschlusszeichen ein `.` , `->`während in C++ das Zeichen entweder ein oder ein ist. Der Triggerwert wird festgelegt, wenn das Elementauswahlzeichen gescannt wird.

### <a name="the-intellisense-member-list-command"></a>Das IntelliSense-Memberlisten-Kommando

Der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Befehl initiiert einen <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Aufruf der <xref:Microsoft.VisualStudio.Package.Source> Methode <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> für die Klasse, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> und die Methode ruft wiederum den Methodenparser mit dem Parse-Grund von [ParseReason.DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>)auf.

Der Parser bestimmt den Kontext der aktuellen Position sowie das Token unter oder unmittelbar vor der aktuellen Position. Basierend auf diesem Token wird eine Liste der Deklarationen angezeigt. Wenn Sie z. B. die Einserstelle auf einem Klassenmitglied positionieren und **Listenmitglieder**auswählen, erhalten Sie eine Liste aller Mitglieder der Klasse. Wenn Sie die Einsparung nach einem Punkt positionieren, der auf eine Objektvariable folgt, erhalten Sie eine Liste aller Member der Klasse, die das Objekt darstellt. Beachten Sie, dass die Auswahl eines Mitglieds aus der Liste das Mitglied ersetzt, auf dem sich die Einserstelle befindet, wenn sie auf einem Mitglied positioniert wird, wenn die Mitgliederliste angezeigt wird.

### <a name="the-token-trigger"></a>Der Token-Trigger

Der [TokenTriggers.MemberSelect-Trigger](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) initiiert einen <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Aufruf <xref:Microsoft.VisualStudio.Package.Source> der Methode <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> für die Klasse, und die Methode ruft wiederum den Parser mit dem Parse-Grund von [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>)auf. Wenn der Token-Trigger auch das [TokenTriggers.MatchBraces-Flag](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) enthält, lautet der Parse-Grund [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), das Elementauswahl und Brace-Hervorhebung kombiniert.

Der Parser bestimmt den Kontext der aktuellen Position sowie das, was vor der Elementauswahl eingegeben wurde. Aus diesen Informationen erstellt der Parser eine Liste aller Member des angeforderten Bereichs. Diese Liste der Deklarationen wird in <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> dem Objekt gespeichert, das von der Methode zurückgegeben wird. Wenn Deklarationen zurückgegeben werden, wird die Tipp zum Memberabschluss angezeigt. Die Tooltip wird von einer <xref:Microsoft.VisualStudio.Package.CompletionSet> Instanz der Klasse verwaltet.

## <a name="enable-support-for-member-completion"></a>Unterstützung für die Mitgliedervervollständigung aktivieren

Sie müssen `CodeSense` den Registrierungseintrag auf 1 festgelegt haben, um alle IntelliSense-Operationen zu unterstützen. Dieser Registrierungseintrag kann mit einem benannten <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Parameter festgelegt werden, der an das Benutzerattribut übergeben wird, das dem Sprachpaket zugeordnet ist. Die Sprachdienstklassen lesen den Wert dieses <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Registrierungseintrags aus der Eigenschaft in der <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse.

Wenn Ihr Scanner den Token-Trigger [von TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)zurückgibt und Ihr Parser eine Liste von Deklarationen zurückgibt, wird die Mitgliederabschlussliste angezeigt.

## <a name="support-member-completion-in-the-scanner"></a>Support-Member-Abschluss im Scanner

Der Scanner muss in der Lage sein, ein Elementabschlusszeichen zu erkennen und den Token-Trigger von [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) festzulegen, wenn dieses Zeichen analysiert wird.

### <a name="scanner-example"></a>Scannerbeispiel

Hier ist ein vereinfachtes Beispiel für das Erkennen <xref:Microsoft.VisualStudio.Package.TokenTriggers> des Memberabschlusszeichens und das Festlegen des entsprechenden Flags. Dieses Beispiel dient nur zur Veranschaulichung. Es wird davon ausgegangen, `GetNextToken` dass Ihr Scanner eine Methode enthält, die Token aus einer Textzeile identifiziert und zurückgibt. Der Beispielcode legt den Trigger einfach fest, wenn er die richtige Art von Zeichen sieht.

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

## <a name="support-member-completion-in-the-parser"></a>Support-Mitglied-Abschluss im Parser

Zur Membervervollständigung <xref:Microsoft.VisualStudio.Package.Source> ruft <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> die Klasse die Methode auf. Sie müssen die Liste in einer Klasse <xref:Microsoft.VisualStudio.Package.Declarations> implementieren, die von der Klasse abgeleitet ist. Weitere <xref:Microsoft.VisualStudio.Package.Declarations> Informationen zu den Methoden, die Sie implementieren müssen, finden Sie in der Klasse.

Der Parser wird mit [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) oder [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) aufgerufen, wenn ein Memberauswahlzeichen eingegeben wird. Die im <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt angegebene Position befindet sich unmittelbar nach dem Elementauswahlzeichen. Der Parser muss die Namen aller Member sammeln, die an diesem bestimmten Punkt im Quellcode in einer Mitgliederliste angezeigt werden können. Anschließend muss der Parser die aktuelle Zeile analysieren, um den Bereich zu bestimmen, den der Benutzer dem Elementauswahlzeichen zugeordnet haben soll.

Dieser Bereich basiert auf dem Typ des Bezeichners, bevor das Element zeichen auswählt. Zum Beispiel in C-Wert, `languageService` wenn die Membervariable mit dem Typ von `LanguageService`, languageService eingibt. **languageService.** erstellt eine Liste aller Member `LanguageService` der Klasse. Auch in C- und **Eingabe.** erstellt eine Liste aller Member der Klasse im aktuellen Bereich.

### <a name="parser-example"></a>Parser-Beispiel

Das folgende Beispiel zeigt eine Möglichkeit <xref:Microsoft.VisualStudio.Package.Declarations> zum Auffüllen einer Liste. Dieser Code setzt voraus, dass der Parser eine Deklaration erstellt und sie der Liste hinzufügt, indem er eine `AddDeclaration` Methode für die `TestAuthoringScope` Klasse aufruft.

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

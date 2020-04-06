---
title: Brace Matching in einem Legacy-Sprachdienst | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0081be3e3ab5a53f7d85f77475d4288aa5c87092
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709817"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Brace-Matching in einem älteren Sprachdienst
Beim Brace-Abgleich kann der Entwickler Sprachelemente nachverfolgen, die zusammen auftreten müssen, z. B. Klammern und geschweifte Klammern. Wenn ein Entwickler eine schließende geschweifte Klammer eingibt, wird die öffnende geschweifte Klammer hervorgehoben.

 Sie können zwei oder drei mitvorkommende Elemente, die als Paare und Triples bezeichnet werden, übereinstimmen. Triples sind Sätze von drei gemeinsam vorkommenden Elementen. `foreach` Die Anweisung bildet z. B. in `foreach()` `{`C' `}`ein Triple: , , und . Alle drei Elemente werden hervorgehoben, wenn die schließende geschweifte Klammer eingegeben wird.

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen zur neuen Möglichkeit zum Implementieren von Klammerabgleich finden Sie unter [Walkthrough: Passende geschweifte Klammern](../../extensibility/walkthrough-displaying-matching-braces.md)anzeigen .

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

 Die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse unterstützt sowohl Paare <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> als <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> auch Triples mit den Methoden.

## <a name="implementation"></a>Implementierung
 Der Sprachdienst muss alle übereinstimmenden Elemente in der Sprache identifizieren und dann alle übereinstimmenden Paare suchen. Dies wird in <xref:Microsoft.VisualStudio.Package.IScanner> der Regel durch Implementieren <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> zum Erkennen einer übereinstimmenden Sprache und anschließende Verwendung der Methode zum Abgleichen der Elemente erreicht.

 Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methode ruft den Scanner auf, um die Leitung zu tokenisieren und das Token kurz vor der Einserseinung zurückzugeben. Der Scanner gibt an, dass ein Sprachelementpaar gefunden <xref:Microsoft.VisualStudio.Package.TokenTriggers> wurde, indem ein Token-Triggerwert von für das aktuelle Token gesetzt wurde. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methode <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> ruft die Methode <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> auf, die wiederum die <xref:Microsoft.VisualStudio.Package.ParseReason> Methode mit dem Wert "Analysegrund" aufruft, um das passende Sprachelement zu suchen. Wenn das passende Sprachelement gefunden wird, werden beide Elemente hervorgehoben.

 Eine vollständige Beschreibung, wie die Eingabe einer geschweiften Klammer die Hervorhebung der geschweiften Klammern auslöst, finden Sie im Abschnitt *Beispielanalyseoperation* im Artikel [Legacy language service parser and scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Unterstützung für Klammerabgleich aktivieren
 Das <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Attribut kann die Registrierungseinträge **MatchBraces**, **MatchBracesAtCaret**und **ShowMatchingBrace** festlegen, die die entsprechenden Eigenschaften der <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse festlegen. Spracheinstellungseigenschaften können auch vom Benutzer festgelegt werden.

|Registrierungseintrag|Eigenschaft|BESCHREIBUNG|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Aktiviert den Korsettab.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Aktiviert den Korsettab, wenn sich die Einserrütze bewegt.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Hebt die zugehörige Klammer hervor.|

## <a name="match-conditional-statements"></a>Abgleichen bedingter Anweisungen
 Sie können bedingte Anweisungen `if`wie `else if`, `else`und `#if` `#elif`, `#else` `#endif`oder , , , , auf die gleiche Weise wie übereinstimmende Trennzeichen abgleichen. Sie können die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse unterklassen und eine Methode bereitstellen, die dem internen Array übereinstimmender Elemente Textspannen sowie Trennzeichen hinzufügen kann.

## <a name="set-the-trigger"></a>Festlegen des Triggers
 Das folgende Beispiel zeigt, wie übereinstimmende Klammern, geschweifte Klammern und quadratische Klammern erkannt und der Auslöser dafür im Scanner gesetzt werden. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methode <xref:Microsoft.VisualStudio.Package.Source> für die Klasse erkennt den Trigger und ruft den Parser auf, um das passende Paar zu finden (siehe Abschnitt *Suchen der Übereinstimmung* in diesem Artikel). Dieses Beispiel dient nur zur Veranschaulichung. Es wird davon ausgegangen, `GetNextToken` dass Ihr Scanner eine Methode enthält, die Token aus einer Textzeile identifiziert und zurückgibt.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private const string braces = "()[]{}";
        private Lexer lex;

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar) && token.Length > 0)
                {
                    if (braces.IndexOf(firstChar) != -1)
                    {
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;
                    }
                }
            }
            return foundToken;
        }
```

## <a name="match-the-braces"></a>Passen Sie die Geschweifklammern
 Hier ist ein vereinfachtes Beispiel `{ }` `( )`für `[ ]`das Abgleichen der Sprachelemente , und , und das Hinzufügen ihrer Spannen zum <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt. Dieser Ansatz ist kein empfohlener Ansatz zum Analysieren von Quellcode. es dient nur zur Veranschaulichung.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class Parser
    {
         private IList<TextSpan[]> m_braces;
         public IList<TextSpan[]> Braces
         {
             get { return m_braces; }
         }
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             if IsMatch(braceSpan1, braceSpan2)
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });
         }

         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             //definition for matching here
          }
    }

    public class TestLanguageService : LanguageService
    {
         Parser parser = new Parser();
         Source source = (Source) this.GetSource(req.FileName);

         private AuthoringScope ParseSource(ParseRequest req)
         {
             if (req.Sink.BraceMatching)
             {
                 if (req.Reason==ParseReason.MatchBraces)
                 {
                     foreach (TextSpan[] brace in parser.Braces)
                     {
                         req.Sink.MatchPair(brace[0], brace[1], 1);
                     }
                 }
             }
             return new TestAuthoringScope();
         }
    }
}
```

## <a name="see-also"></a>Weitere Informationen
- [Legacy-Sprachdienstfunktionen](../../extensibility/internals/legacy-language-service-features1.md)
- [Legacy-Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

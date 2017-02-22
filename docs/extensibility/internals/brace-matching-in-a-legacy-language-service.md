---
title: "Zugeh&#246;rige Klammer in einer Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Zugehörige Klammer"
  - "Sprachdienste [Verwaltetes Paketframework], zugehörige Klammer"
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# Zugeh&#246;rige Klammer in einer Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Klammer kann Entwickler Sprachelemente zu verfolgen, die zusammen, wie z. B. Klammern und geschweifte Klammern sein müssen. Wenn ein Entwickler eine schließende geschweifte Klammer eingibt, wird die öffnende geschweifte Klammer hervorgehoben.  
  
 Sie können zwei oder drei gemeinsam auftretende Elemente mit der Bezeichnung Paare und Tripeln übereinstimmen. Tripeln sind drei gemeinsam auftretende Elemente. Zum Beispiel in c\# die `foreach` Anweisung bildet eine dreifach: "`foreach()`","`{`", und "`}`". Alle drei Elemente werden hervorgehoben, wenn die schließende geschweifte Klammer eingegeben wird.  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Weitere Informationen über die neue Methode zum Implementieren von Klammern finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von übereinstimmenden geschweiften Klammern](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
 Die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse unterstützt beide Paare und Tripeln mit der <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> und <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> Methoden.  
  
## Implementierung  
 Der Sprachdienst muss alle übereinstimmenden Elemente in der Sprache zu identifizieren, und suchen Sie dann alle übereinstimmenden Paare. Dies geschieht in der Regel durch die Implementierung <xref:Microsoft.VisualStudio.Package.IScanner> erkennen eine übereinstimmende Sprache, und klicken Sie dann mit der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode, um die Elemente übereinstimmen.  
  
 Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> \-Methode ruft den Scanner für die Zeile mit Token zu versehen und das Token vor der Einfügemarke zurück. Der Scanner gibt an, dass ein Language\-Element\-Paar gefunden wurde, indem die token Trigger Wert <xref:Microsoft.VisualStudio.Package.TokenTriggers> für das aktuelle Token. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methodenaufrufe der <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> \-Methode, die wiederum die <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> Methode mit dem Analysieren Grund <xref:Microsoft.VisualStudio.Package.ParseReason> zum Suchen des entsprechenden Language\-Elements. Wenn die entsprechende Sprachelement gefunden wird, werden beide Elemente hervorgehoben.  
  
 Eine vollständige Beschreibung der wie eine geschweifte Klammer eingeben löst die geschweifte Klammer hervorheben, finden Sie im Abschnitt "Beispiel analysieren Vorgang" im Thema [Ältere Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## Aktivieren der Unterstützung für Klammer  
 Die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Attributsatz können die `MatchBraces`, `MatchBracesAtCaret`, und `ShowMatchingBrace` benannte Parameter, die die entsprechenden Eigenschaften festlegen der <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse. Eigenschaften der Language\-Einstellung können auch vom Benutzer festgelegt werden.  
  
|Registrierungseintrag|Eigenschaft|Beschreibung|  
|---------------------------|-----------------|------------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Ermöglicht das zugehörige Klammer|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Klammer ermöglicht, als die Einfügemarke verschoben.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Hebt die entsprechende geschweifte Klammer.|  
  
## Übereinstimmende bedingte Anweisungen  
 Sie können bedingte Anweisungen, wie z. B. vergleichen `if`, `else if`, und `else`, oder `#if`, `#elif`, `#else`, `#endif`, auf die gleiche Weise als Trennzeichen. Sie können eine Unterklasse der <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse und bieten eine Methode, die Text hinzufügen kann und Trennzeichen in das interne Array von übereinstimmenden Elementen umfasst.  
  
## Festlegen des Triggers  
 Im folgenden Beispiel wird veranschaulicht, wie übereinstimmende Klammern, geschweifte Klammern und quadratische geschweiften Klammern und Festlegen des Triggers für sie in der Scanner zu erkennen. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methode für die <xref:Microsoft.VisualStudio.Package.Source> Klasse den Trigger erkennt und ruft den Parser, um die paarweise finden \(siehe Abschnitt "Übereinstimmung suchen" in diesem Thema\). In diesem Beispiel wird nur zur Veranschaulichung. Es wird davon ausgegangen, dass der Scanner eine Methode enthält `GetNextToken` identifiziert wird und gibt die Token aus einer Textzeile zurück.  
  
```c#  
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
  
## Die geschweiften Klammern Abgleich  
 Hier ist ein vereinfachtes Beispiel für übereinstimmende des Language\-Elemente {} \(\) und \[\] und ihre Spannen zum Hinzufügen der <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt. Dieser Ansatz ist keine empfohlene Vorgehensweise zum Verarbeiten des Quellcodes. Es ist nur zur Veranschaulichung.  
  
```c#  
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
  
## Siehe auch  
 [Legacy\-Dienst\-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)   
 [Ältere Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
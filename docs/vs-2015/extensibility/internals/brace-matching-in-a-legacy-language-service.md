---
title: Zuordnung von geschweiften Klammern in einem Legacysprachdienst | Microsoft-Dokumentation
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
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 70ad3062a4cbbce8ef46c3afe8851382949fe3f3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753210"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Zugehörige Klammer in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Klammer hilft den Entwickler, die Language-Elemente zu verfolgen, die zusammen, wie z. B. Klammern und geschweifte Klammern enthalten sein müssen. Wenn ein Entwickler eine schließende geschweifte Klammer eingibt, wird der öffnenden geschweiften Klammer hervorgehoben.  
  
 Sie können zwei oder drei gemeinsam auftretende Elemente, die sogenannten-Paare und Tripeln zuordnen. Tripeln werden drei gemeinsam auftretende Elemente. Zum Beispiel in c# die `foreach` Anweisung bildet ein Tripel: "`foreach()`","`{`", und "`}`". Alle drei Elemente werden hervorgehoben, wenn die schließende geschweifte Klammer eingegeben wird.  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Um mehr über die neue Methode zum Implementieren der Zuordnung von geschweiften Klammern zu suchen, finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von übereinstimmenden Klammern](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
 Die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse unterstützt beide-Paare und mit Tripeln der <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> und <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> Methoden.  
  
## <a name="implementation"></a>Implementierung  
 Identifizieren alle übereinstimmenden Elemente in der Sprache, und suchen Sie dann auf alle übereinstimmenden Paare muss der Sprachdienst. Dies erfolgt in der Regel durch die Implementierung <xref:Microsoft.VisualStudio.Package.IScanner> erkennen Sie eine passende Sprache, und klicken Sie dann mit der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode, um die Elemente übereinstimmen.  
  
 Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methodenaufrufe für die Überprüfung, um die Zeile mit Token zu versehen und das Token vor der Einfügemarke zurückzugeben. Die Überprüfung gibt an, dass ein Paar der Language-Element gefunden wurde, indem Sie token Trigger Wert <xref:Microsoft.VisualStudio.Package.TokenTriggers> auf das aktuelle Token. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methodenaufrufe der <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> -Methode, die wiederum ruft die <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> -Methode mit der Analyse-Grund-Wert des <xref:Microsoft.VisualStudio.Package.ParseReason> zum Suchen des Elements der entsprechenden Sprache. Wenn das entsprechende Language-Element gefunden wird, werden beide Elemente hervorgehoben.  
  
 Eine vollständige Beschreibung der wie eine geschweifte Klammer eingeben löst die geschweifte Klammer hervorheben, finden Sie im Abschnitt "Beispiel analysiert Vorgang" im Thema [Legacy-Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## <a name="enabling-support-for-brace-matching"></a>Aktivieren der Unterstützung für die Erkennung von zugehörigen Klammern  
 Die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Attributsatz kann die `MatchBraces`, `MatchBracesAtCaret`, und `ShowMatchingBrace` benannte Parameter, die die entsprechenden Eigenschaften festlegen der <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse. Language-Einstellung-Eigenschaften können auch vom Benutzer festgelegt werden.  
  
|Registrierungseintrag|Eigenschaft|Beschreibung|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Ermöglicht das zugehörige Klammer|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Klammer ermöglicht, als die Einfügemarke verschoben wird.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Hebt die übereinstimmende Klammer hervor.|  
  
## <a name="matching-conditional-statements"></a>Übereinstimmende Bedingungsanweisungen  
 Sie können bedingte Anweisungen, wie z. B. zuordnen `if`, `else if`, und `else`, oder `#if`, `#elif`, `#else`, `#endif`, auf die gleiche Weise als Trennzeichen. Sie können eine Unterklasse der <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse, und geben Sie eine Methode, die Text hinzufügen kann und die Trennzeichen, die das interne Array von übereinstimmenden Elementen umfasst.  
  
## <a name="setting-the-trigger"></a>Festlegen des Triggers  
 Das folgende Beispiel zeigt, wie Sie übereinstimmende Klammern, geschweiften und eckigen Klammern und den Trigger für die sie festlegen, in die Überprüfung zu ermitteln. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methode für die <xref:Microsoft.VisualStudio.Package.Source> Klasse den Trigger erkennt und ruft der Parser, um das entsprechende Paar zu finden (siehe Abschnitt "Suche nach der Übereinstimmung" in diesem Thema). In diesem Beispiel ist nur zur Veranschaulichung. Es wird davon ausgegangen, dass Ihre Überprüfung eine Methode enthält `GetNextToken` identifiziert und gibt die Token von einer Textzeile zurück.  
  
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
  
## <a name="matching-the-braces"></a>Entsprechen die geschweiften Klammern  
 Hier ist ein vereinfachtes Beispiel zum Abgleich der Sprache Elemente {} () und [] und zum Hinzufügen zu ihren Spannen der <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt. Dieser Ansatz ist nicht die empfohlene Ansatz zum Analysieren von Quellcode; Es ist nur zur Veranschaulichung.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Legacy-Dienst-Sprachfunktionen](../../extensibility/internals/legacy-language-service-features1.md)   
 [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)


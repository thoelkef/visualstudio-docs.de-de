---
title: Zuordnung von geschweiften Klammern in einem Legacy-Sprachdienst | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c496c65244f0ede0c3a6385f6cf1329479a17c22
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Zuordnung von geschweiften Klammern in einem Legacy-Sprachdienst
Klammer hilft den Entwickler Sprachelemente zu verfolgen, die zusammen, z. B. Klammern und geschweifte Klammern sein müssen. Wenn ein Entwickler eine schließende Klammer eingibt, wird der öffnenden geschweiften Klammer hervorgehoben.  
  
 Sie können zwei oder drei gemeinsam auftretende Elemente mit der Bezeichnung-Paare und Tripeln überein. Tripeln sind Sätze von drei gemeinsam auftretende Elemente. Beispielsweise ist in c# ist die `foreach` Anweisung bildet eine Triple: "`foreach()`","`{`", und "`}`". Alle drei Elemente werden hervorgehoben, wenn die schließende geschweifte Klammer typisiert ist.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Weitere Informationen über die neue Methode für die Zuordnung von geschweiften Klammern zu implementieren, finden Sie unter [Exemplarische Vorgehensweise: Anzeigen von Klammern](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
 Die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse unterstützt beide-Paare und Tripeln mit der <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> und <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> Methoden.  
  
## <a name="implementation"></a>Implementierung  
 Der Sprachdienst muss Identifizieren aller übereinstimmenden Elemente in der Sprache, und suchen Sie alle übereinstimmenden Paare. Dies erfolgt in der Regel durch Implementierung <xref:Microsoft.VisualStudio.Package.IScanner> erkennen eine übereinstimmende Sprache, und klicken Sie dann mit der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode, um die Elemente entsprechen.  
  
 Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methodenaufrufe der Scanner für die Zeile mit Token zu versehen und zurückzugeben, das Token vor der Einfügemarke. Der Scanner gibt an, dass ein Language-Element-Paar gefunden wurde, durch Festlegen eines Werts token Trigger von <xref:Microsoft.VisualStudio.Package.TokenTriggers> auf das aktuelle Token. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methodenaufrufe der <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> -Methode, die wiederum die <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> Methode mit den ursachenwert Analyse der <xref:Microsoft.VisualStudio.Package.ParseReason> entsprechendes Sprachelement gefunden. Wenn die entsprechendes Sprachelement gefunden wird, werden beide Elemente hervorgehoben.  
  
 Eine vollständige Beschreibung der wie eine geschweifte Klammer eingeben löst die geschweifte Klammer hervorheben, finden Sie im Abschnitt "Beispiel analysieren Vorgang" im Thema [Legacy-Sprachdienstparser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## <a name="enabling-support-for-brace-matching"></a>Aktivieren der Unterstützung für Klammer  
 Die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Attribut kann festgelegt die `MatchBraces`, `MatchBracesAtCaret`, und `ShowMatchingBrace` benannte Parameter, die die entsprechenden Eigenschaften festlegen der <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse. Eigenschaften für Sprache-Einstellung können auch vom Benutzer festgelegt werden.  
  
|Registrierungseintrag|Eigenschaft|Beschreibung|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Ermöglicht das zugehörige Klammer|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Klammer ermöglicht, als die Einfügemarke bewegt.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Werden geschweiften Klammer hervorgehoben.|  
  
## <a name="matching-conditional-statements"></a>Übereinstimmende Bedingungsanweisungen  
 Sie können z. B. bedingte Anweisungen entsprechen `if`, `else if`, und `else`, oder `#if`, `#elif`, `#else`, `#endif`, auf die gleiche Weise als Trennzeichen. Sie können eine Unterklasse der <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse, und geben Sie eine Methode, die Text hinzufügen, kann sowie Trennzeichen in das interne Array von übereinstimmenden Elementen umfasst.  
  
## <a name="setting-the-trigger"></a>Festlegen des Triggers  
 Im folgende Beispiel wird gezeigt, wie übereinstimmende Klammern, geschweifte Klammern und eckige Klammern sowie das Festlegen des Triggers dafür in der Scanner erkannt wird. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methode für die <xref:Microsoft.VisualStudio.Package.Source> Klasse des Triggers erkennt und ruft der Parser um übereinstimmendes Paar suchen (siehe Abschnitt "Übereinstimmung suchen" in diesem Thema). In diesem Beispiel wird nur zur Veranschaulichung. Es wird davon ausgegangen, dass der Scanner eine Methode enthält `GetNextToken` , kennzeichnet, und gibt die Token aus einer Zeile des Texts zurück.  
  
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
  
## <a name="matching-the-braces"></a>Zueinander passende Klammern, die  
 Hier ist ein vereinfachtes Beispiel für das Language-Elemente {} () und [] Datenabgleich an und ihre Spannen zum Hinzufügen der <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt. Dieser Ansatz ist keine empfohlene Vorgehensweise zum Analysieren von Quellcode. Es ist nur zur Veranschaulichung.  
  
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
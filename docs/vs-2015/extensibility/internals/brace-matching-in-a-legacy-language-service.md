---
title: Übereinstimmung von Klammern in einem Legacy Sprachdienst | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d6d7243c8032b22f9abe89021af138f638729011
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840891"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Zugehörige Klammer in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Mit der Übereinstimmung mit geschweiften Klammern können Entwickler Sprachelemente nachverfolgen, die gleichzeitig auftreten müssen, z. b. Klammern und geschweifte Klammern. Wenn ein Entwickler eine schließende geschweifte Klammer eingibt, wird die öffnende geschweifte Klammer hervorgehoben.  
  
 Sie können zwei oder drei zusammen vorkommende Elemente, die als Paare und Paare bezeichnet werden, vergleichen. Dreipel sind Sätze von drei nebeneinander vorkommenden Elementen. In c# `foreach` bildet z. b. die-Anweisung einen dreifachen: " `foreach()` ", " `{` " und " `}` ". Alle drei Elemente werden hervorgehoben, wenn die schließende geschweifte Klammer eingegeben wird.  
  
 Legacy Sprachdienste werden als Teil eines VSPackages implementiert, aber die neuere Methode zum Implementieren von Sprachdienst Funktionen ist die Verwendung von MEF-Erweiterungen. Weitere Informationen zur neuen Methode zum Implementieren der geschweiften Klammer finden Sie unter Exemplarische Vorgehensweise [: anzeigen übereinstimmender](../../extensibility/walkthrough-displaying-matching-braces.md)geschweifter Klammern.  
  
> [!NOTE]
> Es wird empfohlen, dass Sie so bald wie möglich mit der Verwendung der neuen Editor-API beginnen. Dadurch wird die Leistung Ihres sprach Dienstanbieter verbessert, und Sie können die neuen Editor-Features nutzen.  
  
 Die <xref:Microsoft.VisualStudio.Package.AuthoringSink> -Klasse unterstützt sowohl Paare als auch mit der <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> -Methode und der- <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> Methode.  
  
## <a name="implementation"></a>Implementierung  
 Der Sprachdienst muss alle übereinstimmenden Elemente in der Sprache identifizieren und dann alle übereinstimmenden Paare finden. Dies wird in der Regel durch Implementieren von <xref:Microsoft.VisualStudio.Package.IScanner> zum Erkennen einer übereinstimmenden Sprache und anschließendes Verwenden der- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode zum Abgleichen der Elemente erreicht.  
  
 Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> -Methode ruft den Scanner auf, um die Zeile zu tokenten und das Token direkt vor der Einfügemarke zurückzugeben. Der Scanner gibt an, dass ein sprach Element paar gefunden wurde, indem ein tokenauslöserwert von <xref:Microsoft.VisualStudio.Package.TokenTriggers> für das aktuelle Token festgelegt wurde. Die- <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methode ruft die- <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> Methode auf, die wiederum die- <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> Methode mit dem Wert der Analyse Ursache von aufruft <xref:Microsoft.VisualStudio.Package.ParseReason> , um das entsprechende sprach Element zu suchen. Wenn das übereinstimmende sprach Element gefunden wird, werden beide Elemente hervorgehoben.  
  
 Eine umfassende Beschreibung der Art und Weise, in der die Eingabe einer geschweifter Klammer die geschweifter Klammer auslöst, finden Sie im Abschnitt "Beispiel für Analyse Vorgang" im Thema [Legacy-Sprachdienst Parser und Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## <a name="enabling-support-for-brace-matching"></a>Aktivieren der Unterstützung für die Übereinstimmung mit Klammern  
 Das <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> -Attribut kann die `MatchBraces` `MatchBracesAtCaret` benannten Parameter, und festlegen `ShowMatchingBrace` , die die entsprechenden Eigenschaften der- <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse festlegen. Die Eigenschaften der Spracheinstellungen können auch vom Benutzer festgelegt werden.  
  
|Registrierungseintrag|Eigenschaft|BESCHREIBUNG|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Aktiviert die geschweifter Klammer|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Aktiviert die geschweifter Klammer, wenn die Einfügemarke verschoben wird.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Hebt die zugehörige Klammer hervor.|  
  
## <a name="matching-conditional-statements"></a>Übereinstimmende bedingte Anweisungen  
 Sie können Bedingungs Anweisungen, wie z `if` . b `else if` .,, und `else` oder `#if` , `#elif` ,, `#else` `#endif` auf die gleiche Weise wie übereinstimmende Trennzeichen vergleichen. Sie können die <xref:Microsoft.VisualStudio.Package.AuthoringSink> -Klasse Unterklassen und eine Methode bereitstellen, mit der Text Spannen und Trennzeichen dem internen Array von übereinstimmenden Elementen hinzugefügt werden können.  
  
## <a name="setting-the-trigger"></a>Festlegen des Auslösers  
 Im folgenden Beispiel wird gezeigt, wie Sie übereinstimmende Klammern, geschweifte Klammern und eckige Klammern erkennen und den Trigger dafür im Scanner festlegen. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> -Methode für die <xref:Microsoft.VisualStudio.Package.Source> -Klasse erkennt den-Aufruf und ruft den Parser auf, um das passende paar zu finden (Weitere Informationen finden Sie im Abschnitt "Suchen der Übereinstimmung" in diesem Thema). Dieses Beispiel dient nur zu Illustrations Zwecken. Dabei wird davon ausgegangen, dass der Scanner eine Methode enthält `GetNextToken` , die Token aus einer Textzeile identifiziert und zurückgibt.  
  
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
  
## <a name="matching-the-braces"></a>Vergleichen der geschweiften Klammern  
 Im folgenden finden Sie ein vereinfachtes Beispiel für das Abgleichen der Sprachelemente {}, () und [] und das Hinzufügen Ihrer spannen zum- <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt. Diese Vorgehensweise wird nicht empfohlen, um Quellcode zu übernehmen. Sie dient nur zu Illustrations Zwecken.  
  
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
 [Funktionen von Legacy Sprachdiensten](../../extensibility/internals/legacy-language-service-features1.md)   
 [Parser und Scanner von Legacysprachdiensten](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

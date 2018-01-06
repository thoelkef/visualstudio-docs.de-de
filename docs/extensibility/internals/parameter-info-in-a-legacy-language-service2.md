---
title: "ParameterInfo in einer Vorgängerversion Sprache Service2 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 69c65fa2691f71b3bb7f115b771a0de83d543f03
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="parameter-info-in-a-legacy-language-service"></a>ParameterInfo in einen Legacy-Sprachdienst
IntelliSense-ParameterInfo wird als QuickInfo angezeigt, in dem die Signatur einer Methode angezeigt, bei der Eingabe der Benutzer die Parameterliste starten Zeichen (in der Regel eine öffnende Klammer) für die Parameterliste der Methode. Jeder Parameter eingegeben wird und die Trennzeichen (in der Regel ein Komma) für den Parameter typisiert ist, wird die QuickInfo aktualisiert, um den nächsten Parameter in Fettdruck angezeigt.  
  
 Die verwaltete Package Framework (MPF) Klassen bieten Unterstützung für die Verwaltung der ParameterInfo QuickInfo an. Parameter starten, Parameter als Nächstes und Endzeichen Parameter, und sie müssen eine Liste mit den Methodensignaturen und der zugehörigen Parameter angeben, muss der Parser erkannt.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Erweiterung des Editors und des Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="implementation"></a>Implementierung  
 Der Parser sollte den Triggerwert festgelegt <xref:Microsoft.VisualStudio.Package.TokenTriggers> wird festgelegt, wenn es sich um eine Liste Anfang des abfrageparameterzeichens (häufig eine öffnende Klammer) findet. Sollte ein <xref:Microsoft.VisualStudio.Package.TokenTriggers> auslösen, wenn er Parametertrennzeichen (häufig ein Komma) findet. Dies bewirkt, dass eine QuickInfo ParameterInfo aktualisiert wird, und zeigen den nächsten Parameter in Fettschrift angezeigt. Der Parser sollte den Triggerwert festgelegt <xref:Microsoft.VisualStudio.Package.TokenTriggers> wenn wenn sucht nach der Liste Ende des abfrageparameterzeichens (häufig eine schließende Klammer).  
  
 Die <xref:Microsoft.VisualStudio.Package.TokenTriggers> Triggerwert initiiert einen Aufruf der <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> Methode, die ihrerseits die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode Parser mit dem Grund Analyse <xref:Microsoft.VisualStudio.Package.ParseReason>. Wenn der Parser feststellt, dass der Bezeichner, die vor die Parameterliste Zeichen einen erkannten Methodennamen, gibt Sie eine Liste der übereinstimmenden Methodensignaturen in der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt. Wenn alle Methodensignaturen gefunden wurden, wird die ParameterInfo QuickInfo mit der ersten Signatur in der Liste angezeigt. Diese QuickInfo wird aktualisiert, wie mehrere der Signatur eingegeben wird. Wenn die Liste Ende des abfrageparameterzeichens typisiert ist, wird die ParameterInfo QuickInfo aus der Ansicht entfernt.  
  
> [!NOTE]
>  Um sicherzustellen, dass die QuickInfo ParameterInfo ordnungsgemäß formatiert wird, müssen Sie die Eigenschaften auf überschreiben die <xref:Microsoft.VisualStudio.Package.Methods> Klasse, um die entsprechenden Zeichen eingeben. Die Basis <xref:Microsoft.VisualStudio.Package.Methods> Klasse geht davon aus einer c#-Methodensignatur Stil. Finden Sie unter der <xref:Microsoft.VisualStudio.Package.Methods> Klasse ausführliche Informationen wie dies erreicht werden kann.  
  
## <a name="enabling-support-for-the-parameter-info"></a>Aktivieren der Unterstützung für die ParameterInfo  
 Um ParameterInfo QuickInfos zu unterstützen, müssen Sie festlegen der `ShowCompletion` benannte Parameter von der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> auf `true`. Der Sprachdienst liest den Wert dieses Registrierungseintrags aus der <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Eigenschaft.  
  
 Darüber hinaus die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> Eigenschaft muss festgelegt werden, um `true` für die ParameterInfo-QuickInfo angezeigt werden.  
  
### <a name="example"></a>Beispiel  
 Hier ist ein vereinfachtes Beispiel einer erkennen die Parameter Liste Zeichen und die entsprechenden Trigger festlegen. In diesem Beispiel wird nur zur Veranschaulichung. Es wird davon ausgegangen, dass der Scanner eine Methode enthält `GetNextToken` , kennzeichnet, und gibt die Token aus einer Zeile des Texts zurück. Der Beispielcode legt die Trigger einfach fest, wenn es erkennt, dass die richtige Art von Zeichen.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char parameterListStartChar = '(';  
        private const char parameterListEndChar   = ')';  
        private const char parameterNextChar      = ',';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (Char.IsPunctuation(c))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                    tokenInfo.EndIndex = index;  
  
                    if (c == parameterListStartChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;  
                    }  
                    else if (c == parameterListNextChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;  
                    else if (c == parameterListEndChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;  
                    }  
                }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Der Parameter-QuickInfo unterstützt in der Parser  
 Die <xref:Microsoft.VisualStudio.Package.Source> Klasse einige Annahmen zum Inhalt der <xref:Microsoft.VisualStudio.Package.AuthoringScope> und <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klassen, wenn der Parameter-QuickInfo angezeigt und aktualisiert wird.  
  
-   Der Parser erhält <xref:Microsoft.VisualStudio.Package.ParseReason> Wenn das Zeichen für den Parameter Liste typisiert ist.  
  
-   Die im angegebenen Speicherort der <xref:Microsoft.VisualStudio.Package.ParseRequest> sofort nach die Parameterliste starten Zeichen werden soll. Der Parser muss die Signaturen der unter Methodendeklarationen, die zu positionieren, und speichern sie in einer Liste in Ihrer Version von Erfassen der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt. Diese Liste enthält den Methodennamen Methode Typ (oder Rückgabetyp), und eine Liste der möglichen Parameter. Diese Liste wird später für die Methodensignatur oder Signaturen, die in der QuickInfo ParameterInfo anzuzeigen durchsucht.  
  
 Analysieren der Parser müssen Sie angegebene Zeile die <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt zum Sammeln von des Namens der Methode, die eingegeben werden und wie weit der Benutzer befindet sich im Parameter eingeben. Dies erfolgt durch den Namen der Methode zum Übergeben der <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> Methode auf die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt und dem anschließenden Aufrufen der <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> Methode, wenn die Parameterliste starten Zeichen analysiert, Aufrufen der <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> Methode beim der Parameterliste nächste Zeichen ist, analysiert und schließlich aufrufenden die <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> Methode, wenn die Liste Ende des abfrageparameterzeichens analysiert wird. Die Ergebnisse der Methodenaufrufen werden verwendet, durch die <xref:Microsoft.VisualStudio.Package.Source> Klasse, um die ParameterInfo QuickInfo entsprechend aktualisieren.  
  
### <a name="example"></a>Beispiel  
 Hier ist eine Textzeile, die der Benutzer eingeben kann. Die Zahlen unterhalb der Linie geben an, welchen Schritt durch den Parser an dieser Position in der Zeile (vorausgesetzt Analysethreads wechselt von links nach rechts) belegt ist. Die Hierbei wird davon ausgegangen, dass alles vor der Zeile bereits für Methodensignaturen, einschließlich der Signatur der Methode "Testfunc" analysiert wurde.  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 Die Schritte, die der Parser akzeptiert werden im folgenden erläutert:  
  
1.  Der Parser ruft <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> mit dem Text "Testfunc".  
  
2.  Der Parser ruft <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  Der Parser ruft <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  Der Parser ruft <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.
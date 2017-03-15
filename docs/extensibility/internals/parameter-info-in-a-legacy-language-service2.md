---
title: "ParameterInfo in einer Vorg&#228;ngerversion Sprache Service2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense, Parameterinfo-QuickInfo"
  - "Sprachdienste [Verwaltetes Paketframework], Parameter Info von IntelliSense"
  - "ParameterInfo (IntelliSense) sowie Unterstützung in Sprachdienste [Verwaltetes Paketframework]"
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# ParameterInfo in einer Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Parameter Info von IntelliSense wird eine QuickInfo, die die Signatur einer Methode anzeigt, wenn der Benutzer die Parameterliste eingibt starten Zeichen \(in der Regel eine öffnende Klammer\) für die Parameterliste der Methode. Jeden Parameter eingegeben wird, und die Trennzeichen \(in der Regel ein Komma\) für den Parameter typisiert ist, wird die QuickInfo aktualisiert, und den nächsten Parameter in Fettdruck angezeigt.  
  
 Die verwalteten Paket Framework \(MPF\)\-Klassen bieten Unterstützung für die Verwaltung der Parameter\-QuickInfo. Der Parser muss erkennen, Parameter starten, Parameter weiter, und das Endzeichen Parameter, und es muss eine Liste von Methodensignaturen und der zugehörigen Parameter angeben.  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Um weitere Informationen finden Sie unter [Erweitern der\-Editor und Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
## Implementierung  
 Der Parser sollte den Triggerwert festgelegt <xref:Microsoft.VisualStudio.Package.TokenTriggers> wird festgelegt, wenn ein Parameter Liste Start\-Zeichen \(häufig eine öffnende Klammer\) gefunden wird. Sollte ein <xref:Microsoft.VisualStudio.Package.TokenTriggers> ausgelöst wird, wenn ein Parametertrennzeichen \(häufig ein Komma\) gefunden wird. Dadurch wird eine QuickInfo ParameterInfo aktualisiert werden, und den nächsten Parameter in Fettschrift angezeigt. Der Parser sollte den Triggerwert festgelegt <xref:Microsoft.VisualStudio.Package.TokenTriggers> Wenn Wenn findet das Parameter Liste End\-Zeichen \(häufig eine schließende Klammer\).  
  
 Die <xref:Microsoft.VisualStudio.Package.TokenTriggers> Triggerwert initiiert einen Aufruf der <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> \-Methode, die wiederum die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode Parser mit dem Grund Parse <xref:Microsoft.VisualStudio.Package.ParseReason>. Wenn der Parser bestimmt, dass der Bezeichner zunächst die Parameterliste Zeichen ein erkannten Methodenname ist, wird eine Liste von Methodensignaturen in der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt. Wenn alle Signaturen gefunden wurden, wird der Parameter\-QuickInfo mit der ersten Signatur in der Liste angezeigt. Diese QuickInfo wird aktualisiert, wie mehrere der Signatur eingegeben wird. Wenn der Parameter Liste letztes Zeichen eingegeben wird, wird die QuickInfo ParameterInfo aus der Ansicht entfernt.  
  
> [!NOTE]
>  Um sicherzustellen, dass die Parameter\-QuickInfo ordnungsgemäß formatiert wird, überschreiben Sie die Eigenschaften auf die <xref:Microsoft.VisualStudio.Package.Methods> Klasse, um die entsprechenden Zeichen eingeben. Die Basis <xref:Microsoft.VisualStudio.Package.Methods> \-Klasse geht davon aus einer c\#\-Methodensignatur Stil. Finden Sie unter der <xref:Microsoft.VisualStudio.Package.Methods> \-Klasse auf, wie dies erreicht werden kann.  
  
## Aktivieren der Unterstützung für die Parameterinformationen  
 Um Parameter QuickInfos zu unterstützen, müssen Sie festlegen der `ShowCompletion` benannte Parameter von der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> auf `true`. Der Sprachdienst liest den Wert dieses Registrierungseintrags aus der <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Eigenschaft.  
  
 Darüber hinaus die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> Eigenschaft muss festgelegt werden, um `true` für den Parameter\-QuickInfo angezeigt werden.  
  
### Beispiel  
 Hier ist ein vereinfachtes Beispiel erkennen die Parameter Liste Zeichen und die entsprechenden Trigger festlegen. In diesem Beispiel wird nur zur Veranschaulichung. Es wird davon ausgegangen, dass der Scanner eine Methode enthält `GetNextToken` identifiziert wird und gibt die Token aus einer Textzeile zurück. Im Beispielcode wird einfach die Trigger, wenn es erkennt, dass die richtige Art von Zeichen.  
  
```c#  
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
  
## Der Parameter\-QuickInfo unterstützt im Parser  
 Die <xref:Microsoft.VisualStudio.Package.Source> Klasse einige Annahmen über den Inhalt der <xref:Microsoft.VisualStudio.Package.AuthoringScope> und <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klassen, wenn der Parameter\-QuickInfo angezeigt und aktualisiert wird.  
  
-   Der Parser erhält <xref:Microsoft.VisualStudio.Package.ParseReason> Wenn das Zeichen für den Parameter Liste eingegeben wird.  
  
-   Der Speicherort der <xref:Microsoft.VisualStudio.Package.ParseRequest> \-Objekt ist, sofort nach die Parameterliste Zeichen beginnen. Der Parser muss die Signaturen aller Methodendeklarationen erhältlich, die position, und speichern sie in einer Liste in Ihrer Version von Sammeln der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt. Diese Liste enthält den Methodennamen Methode Typ \(oder Rückgabetyp\), und eine Liste der möglichen Parameter. Diese Liste wird später für die Signatur der Methode oder die Signaturen in der QuickInfo ParameterInfo angezeigt durchsucht.  
  
 Analysieren der Parser muss die angegebene Zeile der <xref:Microsoft.VisualStudio.Package.ParseRequest> \-Objekt, das den Namen der Methode eingegeben wird und wie weit die Benutzer zu erfassen ist im Parameter eingeben. Dies geschieht durch Übergeben des Namens der Methode, die die <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> Methode auf die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt und dem anschließenden Aufrufen der <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> \-Methode, wenn die Parameterliste starten Zeichen analysiert wird, Aufrufen der <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> \-Methode, wenn das nächste Zeichen des Parameter\-Liste analysiert wird und schließlich rufen die <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> Methode, wenn der Parameter Liste Endzeichen analysiert wird. Die Ergebnisse dieser Methode Aufrufe werden verwendet, durch die <xref:Microsoft.VisualStudio.Package.Source> Klasse, die die Parameter\-QuickInfo entsprechend aktualisiert.  
  
### Beispiel  
 Hier ist eine Textzeile, die der Benutzer eingeben kann. Die Zahlen unterhalb der Linie geben an, welcher Schritt vom Parser an dieser Position in der Zeile \(sofern Analyse wechselt von links nach rechts\) ausgeführt wird. Die Hierbei wird davon ausgegangen, dass alles vor der Zeile für Methodensignaturen, einschließlich der Signatur der Methode "Testfunc" bereits analysiert wurde.  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 Die Schritte, die der Parser akzeptiert werden unten beschrieben:  
  
1.  Der Seitenparser ruft <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> mit dem Text "Testfunc".  
  
2.  Der Seitenparser ruft <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  Der Seitenparser ruft <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  Der Seitenparser ruft <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.
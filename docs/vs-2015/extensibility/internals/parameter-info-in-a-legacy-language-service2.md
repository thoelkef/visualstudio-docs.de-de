---
title: Parameterinformationen in einem Legacysprachdienst 2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd89520cb976cb6deaca957d97f952e4baa71def
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960451"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Parameterinformationen in einem Legacysprachdienst
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IntelliSense-ParameterInfo wird eine QuickInfo, die die Signatur einer Methode anzeigt, wenn der Benutzer die Parameterliste eingibt starten-Zeichen (in der Regel eine öffnende Klammer) der Parameterliste der Methode. Jeder Parameter eingegeben und Trennzeichen (in der Regel ein Komma) für den Parameter typisiert ist, wird die QuickInfo aktualisiert den nächsten Parameter in Fettschrift angezeigt.  
  
 Die verwaltete Package Framework (MPF)-Klassen bieten Unterstützung für die Verwaltung der ParameterInfo-QuickInfo. Der Parser muss erkennen, Parameter starten, Parameter als Nächstes und Endzeichen Parameter, und sie müssen eine Liste von Methodensignaturen und den zugehörigen Parametern angeben.  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Wenn Sie mehr erfahren möchten, finden Sie unter [Erweitern des Editors und Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="implementation"></a>Implementierung  
 Der Parser sollte den Triggerwert festgelegt <xref:Microsoft.VisualStudio.Package.TokenTriggers> wird festgelegt, wenn es sich um einen Parameter Liste Startzeichen (häufig eine öffnende Klammer) findet. Sollte ein <xref:Microsoft.VisualStudio.Package.TokenTriggers> auslösen, wenn der gefundenen Parametertrennzeichen (häufig ein Komma). Dies bewirkt, dass eine ParameterInfo-QuickInfo aktualisiert werden, und zeigen den nächsten Parameter in Fettschrift angezeigt. Der Parser sollte den Triggerwert festgelegt <xref:Microsoft.VisualStudio.Package.TokenTriggers> beim Wenn sucht nach dem Parameter Liste End-Zeichen (häufig eine schließende Klammer).  
  
 Die <xref:Microsoft.VisualStudio.Package.TokenTriggers> Triggerwert initiiert einen Aufruf der <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> -Methode, die wiederum ruft die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode-Parser, mit einem Grund für die Analyse von <xref:Microsoft.VisualStudio.Package.ParseReason>. Wenn der Parser feststellt, dass der Bezeichner, bevor die Parameterliste beginnt Zeichen Methodenname erkannt, wird eine Liste von Methodensignaturen in der <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt. Wenn alle Signaturen gefunden wurden, wird die ParameterInfo-QuickInfo mit der ersten Signatur in der Liste angezeigt. Diese QuickInfo wird aktualisiert, wie mehrere der Signatur eingegeben wird. Wenn der Parameter Liste Endzeichen eingegeben wird, wird die ParameterInfo-QuickInfo aus der Ansicht entfernt.  
  
> [!NOTE]
>  Um sicherzustellen, dass die ParameterInfo-QuickInfo ist ordnungsgemäß formatiert, müssen Sie die Eigenschaften überschreiben, auf die <xref:Microsoft.VisualStudio.Package.Methods> Klasse, um die entsprechenden Zeichen angeben. Die Basis <xref:Microsoft.VisualStudio.Package.Methods> Klasse geht davon aus einer C#-Stil-Methodensignatur. Finden Sie unter den <xref:Microsoft.VisualStudio.Package.Methods> Klasse Einzelheiten, wie dies erreicht werden kann.  
  
## <a name="enabling-support-for-the-parameter-info"></a>Aktivieren der Unterstützung für die Parameterinformationen  
 Um Parameterinformationen, QuickInfos zu unterstützen, müssen Sie festlegen der `ShowCompletion` benannter Parameter, der die <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> zu `true`. Der Sprachdienst liest den Wert dieses Registrierungseintrags aus der <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Eigenschaft.  
  
 Darüber hinaus die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> Eigenschaft muss festgelegt werden, um `true` für die ParameterInfo-QuickInfo angezeigt werden.  
  
### <a name="example"></a>Beispiel  
 Hier ist ein vereinfachtes Beispiel erkennen die Parameter Liste Zeichen, und die entsprechenden Trigger festlegen. In diesem Beispiel ist nur zur Veranschaulichung. Es wird davon ausgegangen, dass Ihre Überprüfung eine Methode enthält `GetNextToken` identifiziert und gibt die Token von einer Textzeile zurück. Der Beispielcode legt die Trigger einfach, wenn es erkennt, dass die richtige Art von Zeichen.  
  
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
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Unterstützen die Parameterinformations-QuickInfo angezeigt, in der Parser  
 Die <xref:Microsoft.VisualStudio.Package.Source> Klasse einige Annahmen über den Inhalt des der <xref:Microsoft.VisualStudio.Package.AuthoringScope> und <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klassen, wenn die ParameterInfo-QuickInfo angezeigt und aktualisiert wird.  
  
- Der Parser erhält <xref:Microsoft.VisualStudio.Package.ParseReason> Wenn das Zeichen für den Parameter Liste eingegeben wird.  
  
- Den Speicherort, der <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt ist, sofort, nachdem die Parameterliste beginnt Zeichen. Der Parser muss die Signaturen aller Methodendeklarationen erhältlich, die zu positionieren, und speichern sie in einer Liste in Ihrer Version von erfasst werden, die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt. Diese Liste enthält den Methodennamen angeben, Methode Typ (oder Rückgabetyp), und eine Liste der möglichen Parameter. Diese Liste wird später für die Signatur der Methode oder die Signaturen in der ParameterInfo-QuickInfo anzeigen durchsucht.  
  
  Der Parser muss die angegebene Zeile klicken Sie dann analysieren die <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt, das den Namen der Methode, die eingegeben wird und wie weit der Benutzer zu erfassen ist, Parameter eingeben. Dies erfolgt durch Übergeben des Namens der Methode, die die <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> Methode für die <xref:Microsoft.VisualStudio.Package.AuthoringSink> und anschließend durch Aufrufen der <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> Methode, wenn die Parameterliste beginnt Zeichen analysiert wird, Aufrufen der <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> Methode bei der Parameterliste nächste Zeichen ist, analysiert und schließlich Aufrufen der <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> Methode, wenn die Liste End parameterzeichen analysiert wird. Die Ergebnisse dieser Methodenaufrufe werden verwendet, durch die <xref:Microsoft.VisualStudio.Package.Source> Klasse, die ParameterInfo-QuickInfo entsprechend aktualisiert.  
  
### <a name="example"></a>Beispiel  
 Hier ist eine Textzeile, die der Benutzer eingeben kann. Die Zahlen unterhalb der Linie geben an, welcher Schritt vom Parser an dieser Position in der Zeile (vorausgesetzt, Analyse wechselt von links nach rechts) ausgeführt wird. Die Hierbei wird davon ausgegangen, dass alles vor der Zeile für Methodensignaturen, einschließlich der Signatur der Methode "Testfunc" bereits analysiert wurde.  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 Die Schritte, die der Parser akzeptiert werden, sind unten beschrieben:  
  
1.  Der Parser ruft <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> mit dem Text "Testfunc".  
  
2.  Der Parser ruft <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  Der Parser ruft <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  Der Parser ruft <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.

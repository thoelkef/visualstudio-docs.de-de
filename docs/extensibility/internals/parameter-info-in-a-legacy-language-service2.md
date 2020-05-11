---
title: Parameterinformationen in einem Legacy Language Service2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2c40c9ca5c038a70714545f4133db0c0dd686d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706745"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Parameterinformationen in einem Legacysprachdienst
IntelliSense Parameter Info ist eine QuickInfo, die die Signatur einer Methode anzeigt, wenn der Benutzer das Parameterlistenstartzeichen (in der Regel eine offene Klammer) für die Methodenparameterliste eingibt. Wenn jeder Parameter eingegeben wird und das Parametertrennzeichen (in der Regel ein Komma) eingegeben wird, wird die QuickInfo aktualisiert, um den nächsten Parameter fett anzuzeigen.

 Die MPF-Klassen (Managed Package Framework) unterstützen die Verwaltung des Tooltips "Parameterinfo". Der Parser muss Parameterstart, Parameter next und Parameterendzeichen erkennen und eine Liste der Methodensignaturen und der zugehörigen Parameter bereitstellen.

 Ältere Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Möglichkeit zum Implementieren von Sprachdienstfunktionen besteht darin, MEF-Erweiterungen zu verwenden. Weitere Informationen finden Sie unter [Erweitern des Editors und der Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Es wird empfohlen, die neue Editor-API so schnell wie möglich zu verwenden. Dadurch wird die Leistung Ihres Sprachdienstes verbessert und Sie können die neuen Editorfunktionen nutzen.

## <a name="implementation"></a>Implementierung
 Der Parser sollte festlegen, dass der Triggerwert <xref:Microsoft.VisualStudio.Package.TokenTriggers> festgelegt wird, wenn er ein Parameterlistenstartzeichen findet (häufig eine offene Klammer). Es sollte <xref:Microsoft.VisualStudio.Package.TokenTriggers> einen Trigger setzen, wenn ein Parametertrennzeichen (häufig ein Komma) gefunden wird. Dadurch wird eine Parameterinfo-Tooltip aktualisiert und der nächste Parameter fett dargestellt. Der Parser sollte den <xref:Microsoft.VisualStudio.Package.TokenTriggers> Triggerwert festlegen, wenn das Endzeichen der Parameterliste gefunden wird (häufig eine enge Klammer).

 Der <xref:Microsoft.VisualStudio.Package.TokenTriggers> Triggerwert initiiert einen <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> Aufruf der Methode, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> die wiederum den Methodenparser <xref:Microsoft.VisualStudio.Package.ParseReason>mit einem Parse-Grund von aufruft. Wenn der Parser feststellt, dass der Bezeichner vor dem Parameterlistenstartzeichen ein <xref:Microsoft.VisualStudio.Package.AuthoringScope> erkannter Methodenname ist, gibt er eine Liste übereinstimmender Methodensignaturen im Objekt zurück. Wenn Methodensignaturen gefunden wurden, wird die Parameterinfo-Tooltip mit der ersten Signatur in der Liste angezeigt. Diese QuickInfo wird dann aktualisiert, wenn mehr von der Signatur eingegeben wird. Wenn das Parameterlistenendzeichen eingegeben wird, wird die Werkzeugspitze Parameterinfo aus der Ansicht entfernt.

> [!NOTE]
> Um sicherzustellen, dass die Parameterinfo-Tooltip ordnungsgemäß formatiert ist, müssen Sie die Eigenschaften der <xref:Microsoft.VisualStudio.Package.Methods> Klasse überschreiben, um die entsprechenden Zeichen anzugeben. Die <xref:Microsoft.VisualStudio.Package.Methods> Basisklasse setzt eine Methodensignatur im C-Stil an. Weitere <xref:Microsoft.VisualStudio.Package.Methods> Informationen dazu, wie dies geschehen kann, finden Sie in der Klasse.

## <a name="enabling-support-for-the-parameter-info"></a>Aktivieren der Unterstützung für die Parameterinfo
 Um Parameterinfo-Tooltips zu unterstützen, müssen Sie den `ShowCompletion` benannten Parameter des <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . `true` Der Sprachdienst liest den Wert dieses <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Registrierungseintrags aus der Eigenschaft.

 Darüber hinaus <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> muss die Eigenschaft `true` auf "Parameter Info tooltip" festgelegt werden.

### <a name="example"></a>Beispiel
 Hier ist ein vereinfachtes Beispiel für die Erkennung der Parameterlistenzeichen und das Festlegen der entsprechenden Trigger. Dieses Beispiel dient nur zur Veranschaulichung. Es wird davon ausgegangen, `GetNextToken` dass Ihr Scanner eine Methode enthält, die Token aus einer Textzeile identifiziert und zurückgibt. Der Beispielcode legt die Trigger einfach fest, wenn er die richtige Art von Zeichen sieht.

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Unterstützung des Parameter Info ToolTip im Parser
 Die <xref:Microsoft.VisualStudio.Package.Source> Klasse macht einige Annahmen über <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringSink> den Inhalt der und Klassen, wenn die Parameterinfo-Tooltip angezeigt und aktualisiert wird.

- Der Parser <xref:Microsoft.VisualStudio.Package.ParseReason> wird angegeben, wenn das Parameterlistenstartzeichen eingegeben wird.

- Die im <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt angegebene Position befindet sich unmittelbar nach dem Startzeichen der Parameterliste. Der Parser muss die Signaturen aller an dieser Position verfügbaren Methodendeklarationen <xref:Microsoft.VisualStudio.Package.AuthoringScope> sammeln und in einer Liste in der Version des Objekts speichern. Diese Liste enthält den Methodennamen, den Methodentyp (oder rückgabetyp) und eine Liste möglicher Parameter. Diese Liste wird später nach der Methodensignatur oder den Signaturen durchsucht, die in der Werkzeuginfo-Info-Parameterangezeigt angezeigt werden sollen.

  Der Parser muss dann die vom <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt angegebene Linie analysieren, um den Namen der eingegebenen Methode sowie die Anzahl der Fehler beim Eingeben von Parametern zu erfassen. Dies wird erreicht, indem der <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> Name der <xref:Microsoft.VisualStudio.Package.AuthoringSink> Methode an <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> die Methode für das Objekt übergeben und <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> dann die Methode aufgerufen wird, wenn das <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> Parameterlistenstartzeichen analysiert wird, indem die Methode aufgerufen wird, wenn das nächste Zeichen der Parameterliste analysiert wird, und schließlich die Methode aufruft, wenn das Parameterlistenendzeichen analysiert wird. Die Ergebnisse dieser Methodenaufrufe werden <xref:Microsoft.VisualStudio.Package.Source> von der Klasse verwendet, um die Parameterinfo-Tooltip entsprechend zu aktualisieren.

### <a name="example"></a>Beispiel
 Hier ist eine Textzeile, die der Benutzer eingeben könnte. Die Zahlen unterhalb der Zeile geben an, welcher Schritt der Parser an dieser Position in der Zeile macht (vorausgesetzt, die Analyse bewegt sich von links nach rechts). Hier wird davon ausgegangen, dass alles vor der Zeile bereits auf Methodensignaturen analysiert wurde, einschließlich der Signatur der "testfunc"-Methode.

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Die Schritte, die der Parser ausführt, werden im Folgenden beschrieben:

1. Der Parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> ruft mit dem Text "testfunc" auf.

2. Der Parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>ruft auf.

3. Der Parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>ruft auf.

4. Der Parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>ruft auf.

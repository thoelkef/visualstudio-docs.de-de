---
title: Legacy Language Service Parser und Scanner | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c87f447a4b8bca804d27aae4967f4adaf389c627
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707315"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Parser und Scanner von Legacysprachdiensten
Der Parser ist das Herzstück des Sprachdienstes. Die MPF-Sprachklassen (Managed Package Framework) erfordern einen Sprachparser, um Informationen über den angezeigten Code auszuwählen. Ein Parser trennt den Text in lexikalische Token und identifiziert diese Token dann nach Typ und Funktionalität.

## <a name="discussion"></a>Diskussion
 Im Folgenden handelt es sich um eine C-Methode.

```csharp
namespace MyNamespace
{
    class MyClass
    {
        public void MyFunction(int arg1)
        {
            int var1 = arg1;
        }
    }
}
```

 In diesem Beispiel sind die Token die Wörter und Satzzeichen. Die Arten von Token sind wie folgt.

|Tokenname|Tokentyp|
|----------------|----------------|
|Namespace, Klasse, öffentlich, void, int|Schlüsselwort (keyword)|
|=|Operator|
|{ } ( ) ;|Trennzeichen|
|MyNamespace, MyClass, MyFunction, arg1, var1|Bezeichner|
|Mynamespace|Namespace|
|MyClass|class|
|Myfunction|method|
|arg1|parameter|
|var1|Lokale Variable (local variable)|

 Die Rolle des Parsers besteht darin, die Token zu identifizieren. Einige Token können mehr als einen Typ aufweisen. Nachdem der Parser die Token identifiziert hat, kann der Sprachdienst die Informationen verwenden, um hilfreiche Features bereitzustellen, z. B. Syntaxhervorhebung, Klammerabgleich und intelliSense-Vorgänge.

## <a name="types-of-parsers"></a>Arten von Parsern
 Ein Sprachdienstparser ist nicht identisch mit einem Parser, der als Teil eines Compilers verwendet wird. Diese Art von Parser muss jedoch sowohl einen Scanner als auch einen Parser verwenden, ebenso wie ein Compilerparser.

- Ein Scanner wird verwendet, um Tokentypen zu identifizieren. Diese Informationen werden zur Syntaxhervorhebung und zum schnellen Identifizieren von Tokentypen verwendet, die andere Vorgänge auslösen können (z. B. übereinstimmende Klammern). Dieser Scanner wird <xref:Microsoft.VisualStudio.Package.IScanner> durch die Schnittstelle dargestellt.

- Ein Parser wird verwendet, um die Funktionen und den Umfang der Token zu beschreiben. Diese Informationen werden in IntelliSense-Vorgängen verwendet, um Sprachelemente wie Methoden, Variablen, Parameter und Deklarationen zu identifizieren und Listen von Membern und Methodensignaturen basierend auf dem Kontext bereitzustellen. Dieser Parser wird auch verwendet, um übereinstimmende Sprachelementpaare wie geschweifte Klammern und Klammern zu suchen. Auf diesen Parser <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> wird über <xref:Microsoft.VisualStudio.Package.LanguageService> die Methode in der Klasse zugegriffen.

  Wie Sie einen Scanner und Einen Parser für Ihren Sprachdienst implementieren, liegt bei Ihnen. Es stehen mehrere Ressourcen zur Verfügung, die beschreiben, wie Parser funktionieren und wie Sie einen eigenen Parser schreiben. Außerdem stehen mehrere kostenlose und kommerzielle Produkte zur Verfügung, die bei der Erstellung eines Parsers helfen.

### <a name="the-parsesource-parser"></a>Der ParseSource Parser
 Im Gegensatz zu einem Parser, der als Teil eines Compilers verwendet wird (wo die Token in eine Form von ausführbarem Code konvertiert werden), kann ein Sprachdienstparser aus vielen verschiedenen Gründen und in vielen verschiedenen Kontexten aufgerufen werden. Wie Sie diesen Ansatz <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> in <xref:Microsoft.VisualStudio.Package.LanguageService> der Methode in der Klasse implementieren, liegt bei Ihnen. Es ist wichtig zu beachten, dass die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode in einem Hintergrundthread aufgerufen werden kann.

> [!CAUTION]
> Die <xref:Microsoft.VisualStudio.Package.ParseRequest> Struktur enthält einen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Verweis auf das Objekt. Dieses <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt kann nicht im Hintergrundthread verwendet werden. Tatsächlich können viele der Basis-MPF-Klassen nicht im Hintergrundthread verwendet werden. Dazu gehören <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.ViewFilter>die <xref:Microsoft.VisualStudio.Package.CodeWindowManager> , Klassen und jede andere Klasse, die direkt oder indirekt mit der Ansicht kommuniziert.

 Dieser Parser analysiert in der Regel die gesamte Quelldatei beim ersten <xref:Microsoft.VisualStudio.Package.ParseReason> Aufruf oder wenn der Wert des Analysegrunds angegeben wird. Nachfolgende Aufrufe <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> der Methode behandeln einen kleinen Teil des analysierten Codes und können mithilfe der Ergebnisse des vorherigen vollständigen Analysevorgangs viel schneller ausgeführt werden. Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode kommuniziert die Ergebnisse des Analysevorgangs über die <xref:Microsoft.VisualStudio.Package.AuthoringSink> und-Objekte. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Das <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt wird verwendet, um Informationen für einen bestimmten Analysegrund zu sammeln, z. B. Informationen über die Spannen übereinstimmender geschweiften geschweiften Klammern oder Methodensignaturen mit Parameterlisten. Der <xref:Microsoft.VisualStudio.Package.AuthoringScope> bietet Sammlungen von Deklarationen und Methodensignaturen sowie Unterstützung für die erweiterte Bearbeitungsoption Go To (**Gehe zur Definition**, Gehe zur **Deklaration**, **Gehe zur Referenz**).

### <a name="the-iscanner-scanner"></a>Der IScanner Scanner
 Sie müssen auch einen Scanner <xref:Microsoft.VisualStudio.Package.IScanner>implementieren, der implementiert. Da dieser Scanner jedoch zeilenweise über die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse arbeitet, ist die Implementierung in der Regel einfacher. Am Anfang jeder Zeile gibt der <xref:Microsoft.VisualStudio.Package.Colorizer> MPF der Klasse einen Wert, der als Zustandsvariable verwendet werden soll, die an den Scanner übergeben wird. Am Ende jeder Zeile gibt der Scanner die aktualisierte Zustandsvariable zurück. Der MPF speichert diese Statusinformationen für jede Zeile zwischen, sodass der Scanner mit der Analyse von jeder Zeile aus beginnen kann, ohne am Anfang der Quelldatei beginnen zu müssen. Dieses schnelle Scannen einer einzelnen Zeile ermöglicht es dem Editor, dem Benutzer schnelles Feedback zu geben.

## <a name="parsing-for-matching-braces"></a>Parsing für passende Klammern
 Dieses Beispiel zeigt den Fluss des Steuerelements zum Abgleichen einer schließenden geschweiften geschweiften geschweiften geschweiften geschweiften geschweiften Geschweifstelles, die der Benutzer eingegeben hat. In diesem Prozess wird der Scanner, der für die Farbgebung verwendet wird, auch verwendet, um den Tokentyp zu bestimmen und zu bestimmen, ob das Token einen Übereinstimmungs-Brace-Vorgang auslösen kann. Wenn der Trigger gefunden <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> wird, wird die Methode aufgerufen, um die übereinstimmende geschweifte Klammer zu finden. Schließlich werden die beiden geschweiften Klammern hervorgehoben.

 Obwohl geschweifte Klammern in den Namen von Triggern und Analysegründen verwendet werden, ist dieser Prozess nicht auf tatsächliche geschweifte Klammern beschränkt. Jedes Zeichenpaar, das als übereinstimmendes Paar angegeben ist, wird unterstützt. Beispiele sind ( \< und ), und > sowie [ und ].

 Angenommen, der Sprachdienst unterstützt übereinstimmende geschweifte Klammern.

1. Der Benutzer gibt eine schließende geschweifte geschweifte Geschweifklammer ein.

2. Die geschweifte Klammer wird am Cursor in der Quelldatei eingefügt und der Cursor wird um eins erweitert.

3. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methode <xref:Microsoft.VisualStudio.Package.Source> in der Klasse wird mit der typisierten schließenden Klammer aufgerufen.

4. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methode <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> ruft die <xref:Microsoft.VisualStudio.Package.Source> Methode in der Klasse auf, um das Token an der Position direkt vor der aktuellen Cursorposition abzurufen. Dieses Token entspricht der typisierten schließenden Geschweifklammer).

    1. Die <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Methode <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> ruft die <xref:Microsoft.VisualStudio.Package.Colorizer> Methode für das Objekt auf, um alle Token in der aktuellen Zeile abzurufen.

    2. Die <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Methode <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> ruft die <xref:Microsoft.VisualStudio.Package.IScanner> Methode für das Objekt mit dem Text der aktuellen Zeile auf.

    3. Die <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Methode ruft <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> wiederholt <xref:Microsoft.VisualStudio.Package.IScanner> die Methode für das Objekt auf, um alle Token aus der aktuellen Zeile zu sammeln.

    4. Die <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Methode ruft eine <xref:Microsoft.VisualStudio.Package.Source> private Methode in der Klasse auf, um das Token abzurufen, <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> das die gewünschte Position enthält, und übergibt die Liste der Token, die von der Methode abgerufen werden.

5. Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methode sucht nach einem <xref:Microsoft.VisualStudio.Package.TokenTriggers> Token-Trigger-Flag von <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> für das Token, das von der Methode zurückgegeben wird. D. a. das Token, das die schließende geschweifte Klammer darstellt).

6. Wenn das Trigger-Flag <xref:Microsoft.VisualStudio.Package.TokenTriggers> von <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> gefunden <xref:Microsoft.VisualStudio.Package.Source> wird, wird die Methode in der Klasse aufgerufen.

7. Die <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> Methode startet einen Analysevorgang mit dem <xref:Microsoft.VisualStudio.Package.ParseReason>Analysegrundwert von . Dieser Vorgang ruft <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> letztendlich <xref:Microsoft.VisualStudio.Package.LanguageService> die Methode für die Klasse auf. Wenn die asynchrone Analyse aktiviert ist, erfolgt dieser Aufruf der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode in einem Hintergrundthread.

8. Wenn der Analysevorgang abgeschlossen ist, `HandleMatchBracesResponse` wird in der <xref:Microsoft.VisualStudio.Package.Source> Klasse ein interner Abschlusshandler (auch als Rückrufmethode bezeichnet) aufgerufen. Dieser Aufruf wird automatisch <xref:Microsoft.VisualStudio.Package.LanguageService> von der Basisklasse und nicht vom Parser durchgeführt.

9. Die `HandleMatchBracesResponse` Methode ruft eine Liste von <xref:Microsoft.VisualStudio.Package.AuthoringSink> Spannen aus <xref:Microsoft.VisualStudio.Package.ParseRequest> dem Objekt ab, das im Objekt gespeichert ist. (Eine Spanne <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> ist eine Struktur, die einen Bereich von Zeilen und Zeichen in der Quelldatei angibt.) Diese Liste von Spannen enthält in der Regel zwei Spannen, jeweils eine für die öffnenden und schließenden geschweiften Klammern.

10. Die `HandleBracesResponse` Methode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Methode für das <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt auf, das im Objekt gespeichert ist. Dies hebt die angegebenen Spannen hervor.

11. Wenn <xref:Microsoft.VisualStudio.Package.LanguagePreferences> die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> Eigenschaft aktiviert `HandleBracesResponse` ist, ruft die Methode den Text ab, der von der übereinstimmenden Spanne umschlossen wird, und zeigt die ersten 80 Zeichen dieser Spanne in der Statusleiste an. Dies funktioniert <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> am besten, wenn die Methode das Sprachelement enthält, das dem übereinstimmenden Paar beiliegt. Weitere Informationen finden Sie in den Ausführungen zur <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>-Eigenschaft.

12. Fertig.

### <a name="summary"></a>Zusammenfassung
 Die übereinstimmende Geschweifkraft ist in der Regel auf einfache Paare von Sprachelementen beschränkt. Komplexere Elemente, wie z.`if(...)`B.`{`passende`}`Triples`else`("`{`",`}`" " und " , oder " ", " " und " ), können als Teil eines Wortvervollständigungsvorgangs hervorgehoben werden. Wenn z. B. das Wort "else"`if`beendet ist, kann die entsprechende "" -Anweisung hervorgehoben werden. Wenn es eine `if` / `else if` Reihe von Anweisungen gibt, können alle hervorgehoben werden, indem der gleiche Mechanismus wie übereinstimmende geschweifte Klammern verwendet werden. Die <xref:Microsoft.VisualStudio.Package.Source> Basisklasse unterstützt dies bereits wie folgt: Der <xref:Microsoft.VisualStudio.Package.TokenTriggers> Scanner muss <xref:Microsoft.VisualStudio.Package.TokenTriggers> den Token-Triggerwert in Kombination mit dem Triggerwert für das Token zurückgeben, das sich vor der Cursorposition befindet.

 Weitere Informationen finden Sie unter [Brace Matching in a Legacy Language Service](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Parsing für die Farbgebung
 Das Färben des Quellcodes ist einfach, identifizieren Sie einfach den Tokentyp und geben Sie Farbinformationen zu diesem Typ zurück. Die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse fungiert als Vermittler zwischen dem Editor und dem Scanner, um Farbinformationen zu jedem Token bereitzustellen. Die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse <xref:Microsoft.VisualStudio.Package.IScanner> verwendet das Objekt, um beim Kolorisieren einer Linie zu helfen und auch Statusinformationen für alle Zeilen in der Quelldatei zu sammeln. In den MPF-Sprachdienstklassen muss die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse nicht überschrieben werden, da <xref:Microsoft.VisualStudio.Package.IScanner> sie nur über die Schnittstelle mit dem Scanner kommuniziert. Sie geben das Objekt <xref:Microsoft.VisualStudio.Package.IScanner> an, das <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> die Schnittstelle <xref:Microsoft.VisualStudio.Package.LanguageService> implementiert, indem Sie die Methode für die Klasse überschreiben.

 Der <xref:Microsoft.VisualStudio.Package.IScanner> Scanner erhält über die <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> Methode eine Quellcodezeile. Aufrufe der <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> Methode werden wiederholt, um das nächste Token in der Zeile abzurufen, bis die Zeile von Token erschöpft ist. Für die Farbgebung behandelt der MPF den gesamten Quellcode als eine Sequenz von Zeilen. Daher muss der Scanner in der Lage sein, mit der Quelle fertig zu werden, die als Linien an kommt. Darüber hinaus kann jede Zeile jederzeit an den Scanner übergeben werden, und die einzige Garantie ist, dass der Scanner die Zustandsvariable von der Zeile erhält, bevor die Leitung gescannt werden soll.

 Die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse wird auch verwendet, um Token-Trigger zu identifizieren. Diese Trigger weisen den MPF darauf hin, dass ein bestimmtes Token einen komplexeren Vorgang initiieren kann, z. B. die Wortvervollständigung oder übereinstimmende geschweifte Geschweifstellen. Da die Identifizierung solcher Trigger schnell sein und an jedem Ort erfolgen muss, eignet sich der Scanner am besten für diese Aufgabe.

 Weitere Informationen finden Sie unter [Syntax colorizing in a Legacy Language Service](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Analysieren auf Funktionalität und Umfang
 Das Analysieren auf Funktionalität und Umfang erfordert mehr Aufwand als nur das Identifizieren der Tokentypen, die gefunden werden. Der Parser muss nicht nur den Tokentyp identifizieren, sondern auch die Funktionalität, für die das Token verwendet wird. Ein Bezeichner ist z. B. nur ein Name, aber in Ihrer Sprache kann ein Bezeichner je nach Kontext der Name einer Klasse, eines Namespace, einer Methode oder einer Variablen sein. Der allgemeine Typ des Tokens kann ein Bezeichner sein, aber der Bezeichner kann auch andere Bedeutungen haben, je nachdem, was er ist und wo er definiert ist. Diese Identifizierung erfordert, dass der Parser umfassendere Kenntnisse über die Sprache hat, die analysiert wird. Hier kommt <xref:Microsoft.VisualStudio.Package.AuthoringSink> die Klasse ins Spiel. Die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse sammelt Informationen über Bezeichner, Methoden, übereinstimmende Sprachpaare (z. B. Klammern und Klammern) und Sprach-Triples`foreach()`(ähnlich`{`wie`}`Sprachpaare, außer dass es drei Teile gibt, z. B. " " " " " und " ). Darüber hinaus können Sie <xref:Microsoft.VisualStudio.Package.AuthoringSink> die Klasse überschreiben, um die Codeidentifizierung zu unterstützen, die bei der frühen Validierung von Haltepunkten verwendet wird, so dass der Debugger nicht geladen werden muss, und das Auto-Debuggingfenster, das lokale Variablen und Parameter automatisch anzeigt, wenn ein Programm gedebuggiert wird, und erfordert, dass der Parser zusätzlich zu den vom Debugger dargestellten geeigneten lokalen Variablen und Parametern geeignete lokale Variablen und Parameter identifiziert. **Autos**

 Das <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt wird als Teil des <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekts an <xref:Microsoft.VisualStudio.Package.AuthoringSink> den Parser übergeben, <xref:Microsoft.VisualStudio.Package.ParseRequest> und jedes Mal, wenn ein neues Objekt erstellt wird, wird ein neues Objekt erstellt. Darüber hinaus <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> muss die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Methode ein Objekt zurückgeben, das zum Behandeln verschiedener IntelliSense-Vorgänge verwendet wird. Das <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekt verwaltet eine Liste für Deklarationen und eine Liste für Methoden, die je nach dem Grund für die Analyse aufgefüllt werden. Die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse muss implementiert werden.

## <a name="see-also"></a>Weitere Informationen
- [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Übersicht über Legacysprachdienste](../../extensibility/internals/legacy-language-service-overview.md)
- [Einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Zugehörige Klammer in einem Legacysprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

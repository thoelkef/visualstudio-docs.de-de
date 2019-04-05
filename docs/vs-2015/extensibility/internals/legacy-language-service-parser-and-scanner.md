---
title: Ältere Sprachdienstparser und Scanner | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d5110c0289a630640fdb2c2383234173d931c72
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958346"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Parser und Scanner von Legacysprachdiensten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der Parser ist das Herzstück des Sprachdiensts. Die Managed Package Framework (MPF)-Language-Klassen erfordern einen Sprachenparser auf Informationen über den Code, der angezeigt wird. Ein Parser trennt den Text in lexikalischer Token, und klicken Sie dann identifiziert diese Token nach Typ und Funktion.  
  
## <a name="discussion"></a>Diskussion  
 Im folgenden finden eine C#-Methode.  
  
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
  
 In diesem Beispiel werden die Token an die Wörter und Satzzeichen. Die Arten von Token sind wie folgt aus.  
  
|Tokenname|Tokentyp|  
|----------------|----------------|  
|Namespace "," öffentlich "void"-Klasse, Int|keyword|  
|=|operator|  
|{ } ( ) ;|Trennzeichen (delimiter)|  
|MyNamespace "," MyClass "," MyFunction "," arg1 "," var1|identifier|  
|MyNamespace|namespace|  
|MyClass|Klasse|  
|MyFunction|Methode|  
|arg1|-Parameter von|  
|var1|lokale variable|  
  
 Die Rolle des Parsers werden die Token identifizieren. Token können mehr als einen Typ haben. Nachdem der Parser Token identifiziert wurde, können der Sprachdienst die Informationen zur Verfügung zu stellen hilfreiche Features, wie die syntaxhervorhebung, Klammer, und die IntelliSense-Vorgänge.  
  
## <a name="types-of-parsers"></a>Typen von Parsern  
 Ein Sprachenparser für den Dienst ist nicht identisch mit einen Parser, der als Teil eines Compilers verwendet. Jedoch muss sich diese Art von Parser für die Verwendung eines Scanners und einen Parser, auf die gleiche Weise wie eine Compiler-Parser.  
  
- Ein Scanner wird zum Identifizieren von Tokentypen verwendet. Diese Informationen werden zur syntaxhervorhebung und zum schnellen Identifizieren von Tokentypen, die andere Vorgänge, z. B. auslösen können Zuordnung von geschweiften Klammern verwendet werden. Diese Überprüfung wird dargestellt, durch die <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle.  
  
- Ein Parser wird verwendet, um die Funktionen und Umfang der Token zu beschreiben. Diese Informationen werden in IntelliSense-Vorgänge verwendet, wenn Sie Sprachelemente, z. B. Methoden, Variablen, Parameter und Deklarationen, identifizieren und um Listen von Elementen und Signaturen basierend auf dem Kontext bereitzustellen. Dieser Parser wird auch verwendet, um übereinstimmende Language-Element-Paare, z. B. von geschweiften Klammern und Klammern zu suchen. Dieser Parser erfolgt über die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse.  
  
  Wie Sie einen Scanner und Parser für den Sprachdienst implementieren, bleibt Ihnen überlassen. Einige Ressourcen sind verfügbar, die Funktionsweise von Parser und zum Schreiben eigener Parsers beschreiben. Darüber hinaus sind mehrere kostenlose und kommerzielle Produkte verfügbar, die einen Parser erstellen können.  
  
### <a name="the-parsesource-parser"></a>Der ParseSource Parser  
 Im Gegensatz zu einen Parser, der als Teil eines Compilers verwendet wird (wobei die Token in eine Form von ausführbarem Code konvertiert werden), kann ein sprachdienstparser für viele verschiedene Gründe und in vielen verschiedenen Kontexten aufgerufen werden. Wie Sie diesen Ansatz implementieren die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse bleibt Ihnen überlassen. Es ist wichtig zu bedenken, die die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode kann in einem Hintergrundthread aufgerufen werden.  
  
> [!CAUTION]
>  Die <xref:Microsoft.VisualStudio.Package.ParseRequest> Struktur enthält einen Verweis auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt. Dies <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt kann nicht im Hintergrundthread verwendet werden. Viele der die MPF-Basisklassen können nicht in der Tat im Hintergrundthread verwendet werden. Dazu gehören die <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Klassen und einer beliebigen anderen Klasse, die direkt oder indirekt mit der Ansicht kommuniziert.  
  
 Dieser Parser analysiert in der Regel die gesamte Quelle der ersten Dateizeit Funktion aufgerufen wurde bzw. wenn die Analyse Wert der Grund <xref:Microsoft.VisualStudio.Package.ParseReason> erhält. Nachfolgende Aufrufe der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode einen kleinen Teil des analysierten Code behandeln und die Ergebnisse der vorherigen vollständigen Analysevorgang mit sehr viel schneller ausgeführt werden kann. Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode kommuniziert die Ergebnisse des Analysevorgangs über die <xref:Microsoft.VisualStudio.Package.AuthoringSink> und <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekte. Die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt wird zum Sammeln von Informationen für einen bestimmten Grund analysieren, z. B. Informationen über die Spannen der übereinstimmenden geschweiften Klammern oder Signaturen, die Parameterlisten aufweisen. Die <xref:Microsoft.VisualStudio.Package.AuthoringScope> enthält Auflistungen von Deklarationen und die Methodensignaturen und auch Unterstützung für die erweiterte Gehe zu bearbeiten-Option (**Gehe zu Definition**, **Gehe zu Deklaration**, **finden Sie unter Verweisen auf**).  
  
### <a name="the-iscanner-scanner"></a>Der Scanner IScanner  
 Sie müssen auch einen Scanner, die implementiert implementieren <xref:Microsoft.VisualStudio.Package.IScanner>. Jedoch, da diese Überprüfung pro Zeile für Zeile durch arbeitet die <xref:Microsoft.VisualStudio.Package.Colorizer> -Klasse, es ist in der Regel einfacher zu implementieren. Am Anfang jeder Zeile, die MPF bietet die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse einen Wert als eine State-Variable, die die Überprüfung übergeben werden. Am Ende jeder Zeile gibt die Überprüfung der aktualisierte Zustand Variablen zurück. Das MPF speichert diese Statusinformationen für jede Zeile, damit die Überprüfung kann ohne Starten am Anfang der Quelldatei in eine beliebige Zeile zu analysieren. Diese schnelle Scannen aus einer einzigen Zeile können den Editor, um schnelles Feedback für den Benutzer.  
  
## <a name="parsing-for-matching-braces"></a>Analyse für übereinstimmende geschweifte Klammern  
 Dieses Beispiel zeigt die ablaufsteuerung für den Abgleich eine schließende geschweifte Klammer, die der Benutzer eingegeben hat. In diesem Prozess wird die Überprüfung, die für die farbliche Kennzeichnung dient auch zum Bestimmen den Typ der Token und gibt an, ob das Token einen Übereinstimmung Klammern-Vorgang ausgelöst werden kann. Wenn der Trigger gefunden wird, die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> aufgerufen, um die Klammer zu finden. Schließlich werden die beiden geschweiften Klammern hervorgehoben.  
  
 Obwohl geschweifte Klammern in den Namen der Trigger verwendet werden und Gründe zu analysieren, ist dieser Prozess nicht auf tatsächliche geschweifte Klammern beschränkt. Es wird ein beliebiges Paar von Zeichen, die angegeben wird, ein übereinstimmendes Paar werden unterstützt. Beispiele hierfür sind (und) \< und >, und [und].  
  
 Wird davon ausgegangen Sie, dass der Sprachdienst übereinstimmende geschweiften Klammern unterstützt.  
  
1.  Der Benutzer gibt eine schließende geschweifte Klammer (}).  
  
2.  Die geschweifte Klammer an der Cursorposition in der Quelldatei eingefügt wird, und der Cursor von einem erweitert wird.  
  
3.  Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.Source> Klasse mit der typisierten schließenden geschweiften Klammer aufgerufen wird.  
  
4.  Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methodenaufrufe der <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.Source> Klasse, um das Token an die Position direkt vor der aktuellen Cursorposition abzurufen. Dieses Token entspricht die typisierte schließende geschweifte Klammer).  
  
    1.  Die <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Methodenaufrufe der <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Methode für die <xref:Microsoft.VisualStudio.Package.Colorizer> Objekts, um alle Token in der aktuellen Zeile abzurufen.  
  
    2.  Die <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Methodenaufrufe der <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> Methode für die <xref:Microsoft.VisualStudio.Package.IScanner> Objekt mit dem Text der aktuellen Zeile.  
  
    3.  Die <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Methode wiederholt aufruft der <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> Methode für die <xref:Microsoft.VisualStudio.Package.IScanner> Objekt, das alle Token aus der aktuellen Zeile zu erfassen.  
  
    4.  Die <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Methode ruft eine private Methode in der <xref:Microsoft.VisualStudio.Package.Source> Klasse, um das Token abzurufen, die die gewünschte Position enthält, und übergibt die Liste der Token aus dem <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Methode.  
  
5.  Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methode sucht nach token Trigger Kennzeichen <xref:Microsoft.VisualStudio.Package.TokenTriggers> auf dem Token, die von zurückgegeben wird das <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> -Methode, d. h. das Token, die schließende geschweifte Klammer darstellt).  
  
6.  Wenn der Trigger der flag <xref:Microsoft.VisualStudio.Package.TokenTriggers> gefunden wird, wird die <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> -Methode in der die <xref:Microsoft.VisualStudio.Package.Source> -Klasse aufgerufen wird.  
  
7.  Die <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> Methode startet einen Analysevorgang mit dem Wert des Analyse-Grund der <xref:Microsoft.VisualStudio.Package.ParseReason>. Dieser Vorgang schließlich Ruft die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse. Wenn asynchrone Analyse aktiviert ist, rufen diese auf die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode, die in einem Hintergrundthread auftritt.  
  
8.  Wenn der Analysevorgang abgeschlossen ist, eine interne Abschlusshandler (auch bekannt als eine Rückrufmethode) mit dem Namen `HandleMatchBracesResponse` wird aufgerufen, der <xref:Microsoft.VisualStudio.Package.Source> Klasse. Dieser Aufruf erfolgt automatisch durch die <xref:Microsoft.VisualStudio.Package.LanguageService> Basisklasse nicht vom Parser.  
  
9. Die `HandleMatchBracesResponse` Methode ruft eine Liste von Spannen aus dem <xref:Microsoft.VisualStudio.Package.AuthoringSink> -Objekt, das in gespeichert ist die <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt. (Eine Spanne ist ein <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> -Struktur, die einen Bereich von Zeilen und Zeichen in der Quelldatei angibt.) Die Liste von Spannen enthält in der Regel zwei Spannen, die jeweils eine für die öffnende und schließende geschweifte Klammern.  
  
10. Die `HandleBracesResponse` Methodenaufrufe der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> -Objekt, das in gespeichert ist die <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt. Dadurch werden die angegebenen Spannen hervorgehoben.  
  
11. Wenn die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Eigenschaft <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> aktiviert ist, die `HandleBracesResponse` Methode ruft den Text, der wird durch die entsprechenden Spanne einschließt und die ersten 80 Zeichen der, dass die Spanne in der Statusleiste angezeigt. Dies funktioniert am besten, wenn die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode enthält das Language-Element, das das entsprechende Paar begleitet. Weitere Informationen finden Sie in den Ausführungen zur <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>-Eigenschaft.  
  
12. Fertig.  
  
### <a name="summary"></a>Zusammenfassung  
 Der übereinstimmenden geschweiften Klammern-Vorgang ist in der Regel auf einfache Paare von Sprachelementen beschränkt. Komplexere Elemente wie die übereinstimmende Tripel ("`if(…)`","`{`"und"`}`", oder "`else`","`{`"und"`}`"), kann als Teil eines Vorgangs wortvervollständigung hervorgehoben werden. Wenn z. B. das Wort "else" abgeschlossen ist, den entsprechenden "`if`"-Anweisung kann hervorgehoben werden. Gäbe es eine Reihe von `if` / `else if` Anweisungen, die alle von ihnen mithilfe des gleichen Mechanismus verwenden, als zueinander passende Klammern hervorgehoben werden können. Die <xref:Microsoft.VisualStudio.Package.Source> Basisklasse unterstützt bereits, wie folgt: Die Überprüfung der token Triggerwert zurückgeben muss <xref:Microsoft.VisualStudio.Package.TokenTriggers> in Kombination mit den Triggerwert <xref:Microsoft.VisualStudio.Package.TokenTriggers> für das Token, das vor die Position liegt.  
  
 Weitere Informationen finden Sie unter [Klammer in einem Legacysprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-colorization"></a>Analysieren von ASP.NET-Vorlagen für die farbliche Kennzeichnung  
 Farbliche Kennzeichnung von Quellcode ist einfach, nur den Typ des token und eine Rückgabe Farbinformationen Informationen zu diesem Typ zu identifizieren. Die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse fungiert als Vermittler zwischen dem Editor und die Überprüfung, Farbinformationen über jedes Token bereitstellen. Die <xref:Microsoft.VisualStudio.Package.Colorizer> -Klasse verwendet die <xref:Microsoft.VisualStudio.Package.IScanner> Objekt als Hilfe bei der farbliche Kennzeichnung von einer Zeile sowie zum Sammeln von Informationen für alle Zeilen in der Quelldatei. In die MPF-Language-Dienstklassen die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse muss nicht außer Kraft gesetzt werden, da die Kommunikation mit dem Scanner nur über die <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle. Sie angeben, dass das Objekt, implementiert die <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle durch Überschreiben der <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse.  
  
 Die <xref:Microsoft.VisualStudio.Package.IScanner> Scanner erhält eine Zeile des Quellcodes durch den <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> Methode. Aufrufe von der <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> Methode werden wiederholt, um das nächste Token in der Zeile zu erhalten, bis die Zeile der Token erschöpft ist. Für die farbliche Kennzeichnung behandelt das MPF sämtlichen Quellcode als Sequenz von Zeilen an. Aus diesem Grund muss die Überprüfung mit Quelle, die sich in Form von Linien in bewältigen können. Darüber hinaus zu einem beliebigen Zeitpunkt eine beliebige Zeile, die Überprüfung übergeben werden kann, und es ist nur garantiert, dass die Überprüfung der Statusvariablen erhält, über die Befehlszeile vor der Zeile gesucht werden soll.  
  
 Die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse wird auch verwendet, um das token Auslöser zu identifizieren. Diese Trigger Teilen des MPFS, dass ein bestimmtes Token einen komplexeren Vorgang, z. B. wortvervollständigung initiieren kann oder zueinander passende Klammern. Da solche Trigger identifizieren schnell sein muss und muss an einer beliebigen Position auftreten, ist die Überprüfung für diese Aufgabe am besten geeignet.  
  
 Weitere Informationen finden Sie unter [einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-functionality-and-scope"></a>Analysieren von ASP.NET-Vorlagen für Funktionen und Umfang  
 Analysieren von ASP.NET-Vorlagen für Funktionen und Umfang erfordert mehr Aufwand als lediglich identifizieren die Typen der Token, die aufgetreten sind. Der Parser hat zum Identifizieren nicht nur den Typ des Tokens, sondern auch die Funktionen, die für die das Token verwendet wird. Beispielsweise wird ein Bezeichner ist nur ein Name, aber in Ihrer Sprache, ein Bezeichner ist möglicherweise der Name der Klasse, Namespace, Methode oder Variable, je nach Kontext. Der allgemeine Typ des Tokens kann ein Bezeichner sein, aber die Bezeichner möglicherweise auch andere Bedeutungen, abhängig davon, was es ist, in dem sie definiert ist. Diese Identifikation ist erforderlich, den Parser um umfangreichere Kenntnisse über die Sprache zu erhalten, die analysiert wird. Hier kommt die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse ist. Die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse sammelt Informationen zu Bezeichnern, Methoden, entsprechende Sprachpaare (z. B. von geschweiften Klammern und Klammern) und Language Tripel (ähnlich wie Sprachpaare mit dem Unterschied, dass sind drei Schritte, z. B. "`foreach()`" "`{`"und"`}`"). Darüber hinaus können Sie überschreiben die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse, um die Identifizierung von Code, zu unterstützen, die in frühen Überprüfung von Haltepunkten verwendet wird, sodass der Debugger nicht geladen werden, und die **"Auto"** debugging-Fenster, das lokale anzeigt Variablen und Parametern automatisch Wenn ein Programm ein Debugvorgang durchgeführt wird und muss den Parser zur Identifizierung der entsprechenden lokalen Variablen und Parameter zusätzlich zu den, in dem der Debugger dargestellt.  
  
 Die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt wird an den Parser übergeben, als Teil der <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt und ein neues <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt ist erstellt jedes Mal, eine neue <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt erstellt wird. Darüber hinaus die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methodenrückgabewert muss ein <xref:Microsoft.VisualStudio.Package.AuthoringScope> -Objekt, das verwendet wird, um verschiedene IntelliSense-Vorgänge zu behandeln. Die <xref:Microsoft.VisualStudio.Package.AuthoringScope> -Objekt verwaltet eine Liste der Deklarationen und eine Liste der Methoden, entweder die, je nach Ursache für die Analyse aufgefüllt wird. Die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse implementiert werden muss.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren eines Legacysprachdiensts](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Legacysprachdienste](../../extensibility/internals/legacy-language-service-overview.md)   
 [Einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Zugehörige Klammer in einem Legacysprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

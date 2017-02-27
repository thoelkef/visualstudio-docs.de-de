---
title: "&#196;ltere Sprachdienstparser und Scanner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Parser, Sprachdienste [Verwaltetes Paketframework]"
  - "Sprachdienste [Verwaltetes Paketframework], Parser"
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# &#196;ltere Sprachdienstparser und Scanner
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Der Parser ist das Kernstück des Sprachdiensts. Die Language\-Klassen Managed Package Framework \(MPF\) erfordern ein Sprachenparser, wählen Sie die Informationen über den Code, der angezeigt wird. Ein Parser trennt den Text in lexikalischer Token und dann diesen Token nach Typ und Funktion identifiziert.  
  
## Diskussion  
 Im folgenden finden eine C\#\-Methode.  
  
```c#  
namespace MyNamespace { class MyClass { public void MyFunction(int arg1) { int var1 = arg1; } } }  
```  
  
 In diesem Beispiel sind die Token, die Wörter und Interpunktionszeichen. Die Arten von Token sind wie folgt.  
  
|Wenn Sie den Namen|Tokentyp|  
|------------------------|--------------|  
|Namespace, Klasse, public Void Int|keyword|  
|\=|operator|  
|{ } \( \) ;|Trennzeichen|  
|MyNamespace "," MyClass "," MyFunction "," arg1 "," var1|identifier|  
|MyNamespace|namespace|  
|MyClass|Klasse|  
|MyFunction|Methode|  
|arg1|Parameter|  
|var1|lokale variable|  
  
 Die Rolle des Parsers ist die Token zu identifizieren. Einige Token können mehr als einen Typ aufweisen. Nachdem der Parser die Token identifiziert wurde, können der Sprachdienst die Informationen zur Verfügung zu stellen nützliche Funktionen, z. B. syntaxhervorhebung, Klammer, und die IntelliSense\-Vorgänge.  
  
## Typen von Parsern  
 Ein Dienst Sprachenparser ist nicht identisch mit einem Parser als Teil eines Compilers verwendet. Diese Art der Parser muss jedoch ein Scanner und einen Parser, auf die gleiche Weise wie eine Compiler\-Parser verwenden.  
  
-   Scanner wird verwendet, um die verschiedenen Arten von Token. Diese Informationen werden zur syntaxhervorhebung und zum schnellen Identifizieren von Tokentypen, die andere Vorgänge, z. B. auslösen können übereinstimmende Klammern verwendet. Dieser Scanner wird dargestellt, durch die <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle.  
  
-   Ein Parser wird verwendet, um die Beschreibung der Funktionen und Umfang der Token. Diese Informationen werden in IntelliSense\-Vorgängen Sprachelemente, z. B. Methoden, Variablen, Parameter und Deklarationen, identifizieren und Listen von Elementen und Methodensignaturen anhand des Kontexts verwendet. Dieser Parser wird auch verwendet, um übereinstimmende Language\-Element\-Paare, z. B. geschweifte Klammern und Klammern zu suchen. Dieser Parser erfolgt über die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \-Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse.  
  
 Wie Sie einen Scanner und Parser für Ihre Sprachdienst implementieren, bleibt Ihnen überlassen. Mehrere Ressourcen stehen zur Verfügung, die beschreiben, wie Parser funktionieren und wie Sie einen eigenen Parser schreiben. Darüber hinaus sind mehrere kostenlose und kommerzielle Produkte verfügbar, die einen Parser erstellen können.  
  
### Der ParseSource Parser  
 Im Gegensatz zu einen Parser, der als Teil eines Compilers verwendet wird \(wobei die Token in eine Form von ausführbarem Code konvertiert werden\), kann ein Dienst Sprachenparser vielen anderen Gründen und in vielen verschiedenen Kontexten aufgerufen werden. Die Implementierung dieser Ansatz in der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \-Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse liegt bei Ihnen. Es ist wichtig zu beachten, die die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode kann in einem Hintergrundthread aufgerufen werden.  
  
> [!CAUTION]
>  Die <xref:Microsoft.VisualStudio.Package.ParseRequest> Struktur enthält einen Verweis auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt. Diese <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt kann nicht in den Hintergrund\-Thread verwendet werden. Viele der Basisklassen MPF können nicht in der Tat im Hintergrundthread verwendet werden. Dazu gehören die <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Klassen und einer anderen Klasse, die direkt oder indirekt mit der Ansicht kommuniziert.  
  
 Dieser Parser analysiert in der Regel die gesamte Quelle der ersten Dateizeit es aufgerufen wird oder wenn die Analyse Wert Grund <xref:Microsoft.VisualStudio.Package.ParseReason> erhält. Nachfolgende Aufrufe an die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode einen kleinen Teil des analysierten Code behandeln und mit den Ergebnissen des vorherigen vollständigen Analysevorgangs wesentlich schneller ausgeführt werden können. Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode kommuniziert die Ergebnisse des Analysevorgangs über die <xref:Microsoft.VisualStudio.Package.AuthoringSink> und <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekte. Das <xref:Microsoft.VisualStudio.Package.AuthoringSink> \-Objekt wird zum Sammeln von Informationen für einen bestimmten Grund analysieren, z. B. Informationen über die Spannen zueinander passende geschweifte oder Signaturen, die Parameterlisten aufweisen. Die <xref:Microsoft.VisualStudio.Package.AuthoringScope> bietet Sammlungen von Deklarationen und Methodensignaturen und auch Unterstützung für erweiterte Gehe zu bearbeiten\-Option \(**Gehe zu Definition**, **Gehe zu Deklaration**, **Gehe zu Verweis**\).  
  
### Der Scanner IScanner  
 Sie müssen auch einen Scanner, die implementiert implementieren <xref:Microsoft.VisualStudio.Package.IScanner>. Jedoch, da diese operativ pro Zeile für Zeile durch die <xref:Microsoft.VisualStudio.Package.Colorizer> \-Klasse, ist es normalerweise einfacher zu implementieren. Am Anfang jeder Zeile der MPF bietet die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse einen Wert als eine Statusvariable verwendet, der an den Scanner übergeben wird. Am Ende jeder Zeile gibt der Scanner aktualisierte Statusvariable zurück. Die MPF speichert diese Statusinformationen für jede Zeile, damit der Scanner kann in einer beliebigen Zeile ohne am Anfang der Quelldatei zu analysieren. Dieser schnelle aus einer einzigen Zeile Abtastung Editor schnell Feedback an den Benutzer zu.  
  
## Abgleichen der Klammern der Analyse  
 Dieses Beispiel zeigt den Ablauf der Steuerung für den Abgleich eine schließende geschweifte Klammer an, die der Benutzer eingegeben hat. Bei diesem Vorgang wird auch der Scanner für die farbliche Kennzeichnung verwendeten verwendet, bestimmen den Typ der Token und gibt an, ob das Token einen Übereinstimmung Klammern Vorgang auslösen kann. Wenn der Trigger gefunden wird, die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode wird aufgerufen, um die entsprechende geschweifte Klammer gefunden. Schließlich werden die beiden geschweiften Klammern hervorgehoben.  
  
 Obwohl geschweifte Klammern in Namen von Triggern verwendet werden und Analysieren der Gründe, ist dieser Prozess nicht um tatsächliche geschweifte Klammern beschränkt. Jedes Paar von Zeichen ab, die angegeben wird, werden ein entsprechender koppeln wird unterstützt. Beispiele hierfür sind \(und\), \< und \>, und \[und\].  
  
 Wird davon ausgegangen Sie, dass der Sprachdienst übereinstimmende geschweiften Klammern unterstützt.  
  
1.  Der Benutzer gibt eine schließende geschweifte Klammer \(}\).  
  
2.  Die geschweifte Klammer wird an der Cursorposition in der Quelldatei eingefügt, und der Cursor wird durch eine erweiterte.  
  
3.  Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> \-Methode in der <xref:Microsoft.VisualStudio.Package.Source> Klasse wird mit der typisierten schließenden geschweiften Klammer bezeichnet.  
  
4.  Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> \-Methode ruft die <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> \-Methode in der <xref:Microsoft.VisualStudio.Package.Source> Klasse zum Abrufen des Tokens an die Position direkt vor der aktuellen Cursorposition. Dieses Token entspricht die typisierte schließende geschweifte Klammer\).  
  
    1.  Die <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Methodenaufrufe der <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Methode für die <xref:Microsoft.VisualStudio.Package.Colorizer> \-Objekt, das alle Token in der aktuellen Zeile abrufen.  
  
    2.  Die <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> \-Methode ruft die <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> Methode für die <xref:Microsoft.VisualStudio.Package.IScanner> Objekt mit dem Text der aktuellen Zeile.  
  
    3.  Die <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Methodenaufrufe wiederholt die <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> Methode für die <xref:Microsoft.VisualStudio.Package.IScanner> \-Objekt, das alle Token aus der aktuellen Zeile zu sammeln.  
  
    4.  Die <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Methode ruft eine private Methode in der <xref:Microsoft.VisualStudio.Package.Source> Klasse, um das Token zu erhalten, die gewünschte Position enthält, und übergibt die Liste der Token aus der <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Methode.  
  
5.  Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methode sucht ein token Trigger Kennzeichen <xref:Microsoft.VisualStudio.Package.TokenTriggers> auf das Token, das von zurückgegeben wird die <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> \-Methode, d. h. das Token, das die schließende geschweifte Klammer darstellt\).  
  
6.  Wenn der Trigger der flag <xref:Microsoft.VisualStudio.Package.TokenTriggers> gefunden wird, wird die <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> \-Methode in der <xref:Microsoft.VisualStudio.Package.Source> \-Klasse aufgerufen wird.  
  
7.  Die <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> Methode startet einen Analysevorgang mit der Analyse Grund Wert <xref:Microsoft.VisualStudio.Package.ParseReason>. Diesen Vorgang letztlich Ruft die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse. Wenn asynchrone Analyse aktiviert ist, diese aufrufen, um die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode in einem Hintergrundthread auftritt.  
  
8.  Wenn der Analysevorgang abgeschlossen wird, wird eine interne Abschlusshandler \(auch bekannt als eine Rückrufmethode\) mit dem Namen `HandleMatchBracesResponse` aufgerufen wird, der <xref:Microsoft.VisualStudio.Package.Source> Klasse. Dieser Aufruf erfolgt automatisch durch den <xref:Microsoft.VisualStudio.Package.LanguageService> Basisklasse nicht vom Parser.  
  
9. Die `HandleMatchBracesResponse` Methode ruft eine Liste von Spannen aus dem <xref:Microsoft.VisualStudio.Package.AuthoringSink> \-Objekt, das in gespeichert ist die <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt. \(Ein SPAN\-Tag ist eine <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> \-Struktur, die einen Bereich von Zeilen und Zeichen in der Quelldatei angibt.\) Diese Liste von Spannen enthält in der Regel zwei Spannen, jeweils eine für die öffnende und schließende geschweifte Klammern.  
  
10. Die `HandleBracesResponse` Methodenaufrufe der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> \-Objekt, das in gespeichert ist die <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt. Dadurch wird die angegebenen Spannen hervorgehoben.  
  
11. Wenn die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Eigenschaft <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> aktiviert ist, die `HandleBracesResponse` \-Methode erhält den Text, der durch die entsprechende Spanne umgeben ist und die ersten 80 Zeichen der Bereich umfassen in der Statusleiste angezeigt. Dies funktioniert am besten, wenn die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \-Methode enthält das Language\-Element, das die paarweise begleitet. Weitere Informationen finden Sie in den Ausführungen zur <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>\-Eigenschaft.  
  
12. Geschehen.  
  
### Zusammenfassung  
 Die übereinstimmenden geschweiften Klammern Vorgang ist in der Regel auf einfache Paare von Elementen beschränkt. Komplexere Elemente, z. B. übereinstimmende Tripel \("`if(…)`","`{`"und"`}`", oder "`else`","`{`"und"`}`"\), können als Teil eines Word\-Abschluss hervorgehoben werden. Wenn z. B. das Wort "else" abgeschlossen ist, den entsprechenden "`if`" Anweisung hervorgehoben werden kann. Wenn es eine Reihe von gab `if`\/`else if` Anweisungen, die alle mit dem gleichen Mechanismus als zueinander passende Klammern hervorgehoben werden. Die <xref:Microsoft.VisualStudio.Package.Source> Basisklasse bereits unterstützt möchten, klicken Sie hierzu wie folgt: der Scanner muss den token Triggerwert zurückgeben <xref:Microsoft.VisualStudio.Package.TokenTriggers> zusammen mit den Triggerwert <xref:Microsoft.VisualStudio.Package.TokenTriggers> für das Token, das vor der Cursorposition eingefügt wird.  
  
 Weitere Informationen finden Sie unter [Zugehörige Klammer in einer Legacy\-Sprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## Analyse für die farbliche Kennzeichnung  
 Farbliche Kennzeichnung von Quellcode ist einfach, einfach identifiziert den Typ der token und die return\-Informationen zu diesem Typ. Die <xref:Microsoft.VisualStudio.Package.Colorizer> fungiert als Mittler zwischen der Editor und der Scanner Farbe Informationen über jedes Token bereitstellen. Die <xref:Microsoft.VisualStudio.Package.Colorizer> \-Klasse verwendet die <xref:Microsoft.VisualStudio.Package.IScanner> Objekt zur Unterstützung der farbliche Kennzeichnung von einer Zeile und auch zum Sammeln von Informationen für alle Zeilen in der Quelldatei. In den Klassen der MPF Language Service die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse muss nicht überschrieben werden, da er mit dem Scanner kommuniziert nur über die <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle. Geben Sie das Objekt, implementiert die <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle durch Überschreiben der <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse.  
  
 Die <xref:Microsoft.VisualStudio.Package.IScanner> Scanner erhält eine Zeile des Quellcodes durch die <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> Methode. Aufrufe an die <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> Methode werden wiederholt, um das nächste Token in der Zeile zu erhalten, bis die Zeile des Tokens erschöpft ist. Für die farbliche Kennzeichnung behandelt die MPF sämtlichen Quellcode als Sequenz von Zeilen. Daher muss der Scanner Quelle kommen sie sich als Zeilen bewältigen können. Außerdem jederzeit eine beliebige Zeile an den Scanner übergeben werden kann, und ist nur garantiert, dass der Scanner die Statusvariable aus der Zeile vor der Zeile zu scannenden empfängt.  
  
 Die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse wird außerdem verwendet, um token Auslöser zu identifizieren. Diese Trigger Teilen der MPF, dass ein bestimmtes Token einen komplexeren Vorgang, z. B. Word\-Abschluss initiieren kann oder in Übereinstimmung mit geschweiften Klammern. Da solche Trigger identifizieren schnell sein muss und muss an jedem Ort erfolgen, ist der Scanner für diese Aufgabe am besten geeignet.  
  
 Weitere Informationen finden Sie unter [Farbliche Kennzeichnung von Syntax in einem Legacy\-Sprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## Funktionen und Umfang der Analyse  
 Funktionen und Umfang der Analyse ist aufwändiger als identifiziert nur die Typen von Token, die aufgetreten sind. Der Parser hat zum Identifizieren von nicht nur den Typ des Tokens, sondern auch die Funktionalität für die Token verwendet wird. Angenommen, ein Bezeichner ist nur ein Name, aber in Ihrer Sprache ein Bezeichner ist möglicherweise der Name der Klasse, Namespace, Methode oder Variable, je nach Kontext. Der allgemeine Typ des Tokens kann ein Bezeichner sein, aber der Bezeichner möglicherweise eine andere Bedeutung, je nachdem was und definiert wird. Diese Identifikation erfordert den Parser von umfangreichere Kenntnisse über die Sprache, die analysiert wird. Hier kommt die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse ins Spiel. Die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse sammelt Informationen zu Bezeichnern, Methoden, übereinstimmende Sprachpaare \(z. B. geschweifte Klammern und Klammern\) und Language Tripel \(ähnelt Sprachpaare es mich sind drei Teile, z. B. "`foreach()`" "`{`"und"`}`"\). Darüber hinaus können Sie überschreiben die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse, um die Kennung, unterstützen das in frühen Überprüfung der Haltepunkte verwendet wird, damit der Debugger nicht geladen werden, und die **Auto** Debugfenster, das automatisch anzeigt, lokale Variablen und Parameter, wenn eine Anwendung gedebuggt wird, und erfordert den Parser zum Identifizieren der entsprechenden lokalen Variablen und Parameter zusätzlich zu den, in dem der Debugger dargestellt.  
  
 Die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt wird an den Parser übergeben, als Teil der <xref:Microsoft.VisualStudio.Package.ParseRequest> \-Objekt und ein neues <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt erstellt jedes Mal, eine neue <xref:Microsoft.VisualStudio.Package.ParseRequest> \-Objekt wird erstellt. Darüber hinaus die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode zurückgeben muss ein <xref:Microsoft.VisualStudio.Package.AuthoringScope> \-Objekt, das verwendet wird, um verschiedene IntelliSense\-Vorgänge zu behandeln. Die <xref:Microsoft.VisualStudio.Package.AuthoringScope> \-Objekt verwaltet eine Liste für Deklarationen und eine Liste für Methoden, entweder die, abhängig von den Grund für die Analyse aufgefüllt ist. Die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse implementiert werden muss.  
  
## Siehe auch  
 [Implementieren einer Legacy\-Sprachdienst](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Ältere Sprache Service\-Übersicht](../../extensibility/internals/legacy-language-service-overview.md)   
 [Farbliche Kennzeichnung von Syntax in einem Legacy\-Sprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Zugehörige Klammer in einer Legacy\-Sprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
---
title: "Ältere Sprachdienstparser und Scanner | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: c95dbbeaf9dcd6e1014ce3d2af8a0398c6627fe3
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="legacy-language-service-parser-and-scanner"></a>Ältere Sprachdienstparser und Scanner
Der Parser ist das Kernstück des Sprachdiensts. Das Managed Package Framework (MPF) Sprache-Klassen erfordern eine Sprachenparser auf Informationen über den Code, der angezeigt wird. Ein Parser trennt den Text in lexikalische Token, und es werden diese Token nach Typ und Funktion identifiziert.  
  
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
  
 In diesem Beispiel werden die Token an die Wörter und Satzzeichen besteht. Die Arten von Token sind wie folgt aus.  
  
|Tokenname|Tokentyp|  
|----------------|----------------|  
|Namespace, Klasse, öffentlich ist, als "void", Int|keyword|  
|=|operator|  
|{ } ( ) ;|Trennzeichen|  
|MyNamespace "," MyClass "," MyFunction "," arg1 "," var1|identifier|  
|MyNamespace|namespace|  
|MyClass|Klasse|  
|MyFunction|Methode|  
|arg1|Parameter|  
|var1|lokale variable|  
  
 Die Rolle des Parsers ist die Token identifizieren. Einige Token können es sich um mehr als einen Typ aufweisen. Nachdem der Parser das Token identifiziert wurde, können der Sprachdienst die Informationen zur Verfügung zu stellen nützliche Funktionen, z. B. syntaxhervorhebung, Klammer, und die IntelliSense-Vorgänge.  
  
## <a name="types-of-parsers"></a>Typen von Parser  
 Eine sprachdienstparser ist nicht identisch mit einem Parser, der als Teil eines Compilers verwendet. Diese Art von Parser muss jedoch ein Scanner und ein Parser auf die gleiche Weise wie eine Compiler-Parser verwenden.  
  
-   Ein Scanner wird verwendet, um die Identifizierung der Tokentypen. Diese Informationen werden zur syntaxhervorhebung und zum schnellen Identifizieren von Tokentypen, die andere Vorgänge, z. B. auslösen können übereinstimmende Klammern verwendet werden. Dieser Scanner wird dargestellt, indem die <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle.  
  
-   Ein Parser wird verwendet, um die Beschreibung der Funktionen und des Bereichs von Token. Diese Informationen werden in IntelliSense-Vorgängen verwendet, um Sprachelemente wie Methoden, Variablen, Parameter und Deklarationen zu identifizieren und Listen von Elementen und Methodensignaturen anhand des Kontexts bereitstellen. Dieser Parser wird auch verwendet, um übereinstimmende Language-Element-Paare, z. B. geschweifte Klammern und Klammern zu suchen. Dieser Parser erfolgt über die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse.  
  
 Wie Sie einen Scanner und Parser für Ihren Sprachdienst implementieren liegt bei Ihnen. Mehrere Ressourcen verfügbar sind, die beschreiben, wie Parser funktionieren und wie Sie eigene Parser schreiben. Darüber hinaus mehrere kostenlose und kostenpflichtige-Produkte verfügbar sind, die einen Parser erstellen können.  
  
### <a name="the-parsesource-parser"></a>Der ParseSource Parser  
 Im Gegensatz zu einem Parser, der als Teil eines Compilers verwendet wird (wobei die Token in eine Form von ausführbarem Code konvertiert werden), kann eine sprachdienstparser für viele verschiedene Ursachen und in vielen verschiedenen Kontexten aufgerufen werden. Wie Sie diesen Ansatz in implementieren die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode in der <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse liegt bei Ihnen. Es ist wichtig zu bedenken, die die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode kann in einem Hintergrundthread aufgerufen werden.  
  
> [!CAUTION]
>  Die <xref:Microsoft.VisualStudio.Package.ParseRequest> Struktur enthält einen Verweis auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt. Dies <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Objekt kann nicht im Hintergrundthread verwendet werden. In der Tat können viele MPF-Basisklassen im Hintergrundthread verwendet werden. Dazu gehören die <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Klassen und jede andere Klasse, die direkt oder indirekt mit der Ansicht kommuniziert.  
  
 Diese-Parser analysiert in der Regel die gesamte Quelle der ersten Dateizeit aufgerufen wird oder wenn die Analyse Wert der Ursachencode <xref:Microsoft.VisualStudio.Package.ParseReason> erhält. Nachfolgende Aufrufe der <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode einen kleinen Teil der analysierten Code behandeln und von anhand der Ergebnisse der vorherigen vollständigen Analysevorgang wesentlich schneller ausgeführt werden können. Die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode kommuniziert die Ergebnisse des Analysevorgangs über die <xref:Microsoft.VisualStudio.Package.AuthoringSink> und <xref:Microsoft.VisualStudio.Package.AuthoringScope> Objekte. Die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt wird zum Sammeln von Informationen für einen bestimmten Grund analysieren, z. B. Informationen zu den Spannen von zueinander passende geschweifte oder Methodensignaturen, die Parameterlisten aufweisen. Die <xref:Microsoft.VisualStudio.Package.AuthoringScope> bietet Auflistungen von Deklarationen und Methodensignaturen und auch Unterstützung für erweiterte Gehe zu bearbeiten-Option (**Gehe zu Definition**, **Gehe zu Deklaration**, **wechseln Sie zu Verweisen auf**).  
  
### <a name="the-iscanner-scanner"></a>Der Scanner IScanner  
 Sie müssen auch einen Scanner, die implementiert implementieren <xref:Microsoft.VisualStudio.Package.IScanner>. Jedoch, da diese operativ regelmäßig zeilenweise, über die <xref:Microsoft.VisualStudio.Package.Colorizer> -Klasse, es ist in der Regel einfacher zu implementieren. Am Anfang jeder Zeile des verwalteten Paketframeworks bietet die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse einen Wert, der als eine Statusvariable verwendet, die an der Scanner übergeben wird. Am Ende jeder Zeile gibt der Scanner die Statusvariable aktualisiert. Das MPF speichert diese Statusinformationen für jede Zeile, damit der Scanner starten kann aus jeder Zeile analysieren, ohne am Anfang der Quelldatei zu starten. Der Editor zum Bereitstellen von schnellen Feedback an den Benutzer ermöglicht es, wenn Sie dieses schnellen Durchsuchen von einer einzelnen Zeile.  
  
## <a name="parsing-for-matching-braces"></a>Analysieren von zugehöriger geschweifter Klammern  
 Dieses Beispiel zeigt die ablaufsteuerung für den Abgleich eine schließende geschweifte Klammer, die der Benutzer eingegeben hat. In diesem Prozess wird auch der Scanner für die farbliche Kennzeichnung verwendeten verwendet, um zu bestimmen, den Typ der Token und gibt an, ob das Token eine Übereinstimmung Klammer Operation ausgelöst werden kann. Wenn der Trigger gefunden wird, die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode wird aufgerufen, um die übereinstimmende Klammer suchen. Schließlich werden die beiden geschweiften Klammern hervorgehoben.  
  
 Obwohl geschweifte Klammern, die in den Namen von Triggern verwendet werden und analysieren die Gründe, ist dieser Vorgang nicht auf tatsächliche Klammern begrenzt. Ein beliebiges Paar von Zeichen an, die angegeben wird, werden ein entsprechender gekoppelt wird unterstützt. Beispiele hierfür sind (und), \< und >, und [und].  
  
 Wird davon ausgegangen Sie, dass der Sprachdienst Klammern unterstützt.  
  
1.  Der Benutzer gibt eine schließende geschweifte Klammer (}).  
  
2.  Der geschweiften Klammer wird an den Cursor in der Quelldatei eingefügt, und der Cursor wird von einem vorgerückt.  
  
3.  Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methode in der <xref:Microsoft.VisualStudio.Package.Source> Klasse mit den typisierten schließende Klammer aufgerufen wird.  
  
4.  Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methodenaufrufe der <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Methode in der <xref:Microsoft.VisualStudio.Package.Source> Klasse, die Token an die Position unmittelbar vor der aktuellen Cursorposition zu erhalten. Dieses Token entspricht die typisierte schließende geschweifte Klammer).  
  
    1.  Die <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Methodenaufrufe der <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Methode für die <xref:Microsoft.VisualStudio.Package.Colorizer> Objekt, das alle Token in der aktuellen Zeile abrufen.  
  
    2.  Die <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Methodenaufrufe der <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> Methode für die <xref:Microsoft.VisualStudio.Package.IScanner> Objekt mit dem Text der aktuellen Zeile.  
  
    3.  Die <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Methodenaufrufe wiederholt die <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> Methode für die <xref:Microsoft.VisualStudio.Package.IScanner> Objekt, das alle Token aus der aktuellen Zeile zu erfassen.  
  
    4.  Die <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Methode ruft eine private Methode in der <xref:Microsoft.VisualStudio.Package.Source> Klasse, um das Token abzurufen, die die gewünschte Position enthält, und übergibt in der Liste der Token aus dem <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Methode.  
  
5.  Die <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Methode sucht ein token Trigger-Flag von <xref:Microsoft.VisualStudio.Package.TokenTriggers> auf dem Token, die von zurückgegeben wird die <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> -Methode, d. h. das Token, das die schließende geschweifte Klammer darstellt).  
  
6.  Wenn der Trigger der kennzeichnen <xref:Microsoft.VisualStudio.Package.TokenTriggers> gefunden wird, wird die <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> Methode in der <xref:Microsoft.VisualStudio.Package.Source> -Klasse aufgerufen wird.  
  
7.  Die <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> Methode startet einen Analysevorgang mit den ursachenwert Analyse der <xref:Microsoft.VisualStudio.Package.ParseReason>. Dieser Vorgang schließlich Ruft die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse. Wenn die asynchrone Analyse aktiviert ist, aufzurufen die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode in einem Hintergrundthread auftritt.  
  
8.  Wenn der Analysevorgang abgeschlossen wird, wird eine interne Abschlusshandler (auch bekannt als eine Rückrufmethode) mit dem Namen `HandleMatchBracesResponse` wird aufgerufen, der <xref:Microsoft.VisualStudio.Package.Source> Klasse. Dieser Aufruf erfolgt automatisch durch die <xref:Microsoft.VisualStudio.Package.LanguageService> -Basisklasse nicht vom Parser.  
  
9. Die `HandleMatchBracesResponse` Methode ruft eine Liste von Spannen aus der <xref:Microsoft.VisualStudio.Package.AuthoringSink> -Objekt, das in gespeichert ist die <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt. (Eine Spanne ist eine <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> -Struktur, eine Reihe von Zeilen und die Zeichen in der Quelldatei angibt.) Diese Liste von Spannen enthält in der Regel zwei Spannen, jeweils eine für die öffnende und schließende geschweifte Klammern.  
  
10. Die `HandleBracesResponse` Methodenaufrufe der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> -Objekt, das in gespeichert ist die <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt. Dadurch wird die angegebenen Spannen hervorgehoben.  
  
11. Wenn die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Eigenschaft <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> aktiviert ist, die `HandleBracesResponse` -Methode erhält den Text, der durch die entsprechende Spanne enthalten ist und die ersten 80 Zeichen dieser Spanne in der Statusleiste angezeigt. Dies funktioniert am besten, wenn die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methode enthält das Language-Element, das die übereinstimmendes Paar begleitet. Weitere Informationen finden Sie in den Ausführungen zur <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>-Eigenschaft.  
  
12. Geschehen.  
  
### <a name="summary"></a>Zusammenfassung  
 Die Suche nach Übereinstimmungen geschweifte Klammern ist in der Regel auf einfache Paare von Sprachelementen beschränkt. Komplexere Elemente, z. B. übereinstimmende Tripel ("`if(...)`","`{`"und"`}`", oder "`else`","`{`"und"`}`"), können als Teil eines wortvervollständigung Vorgangs hervorgehoben werden. Wenn z. B. das Wort "sonst" abgeschlossen ist, den entsprechenden "`if`" Anweisung hervorgehoben werden kann. Wenn gab es eine Reihe von `if` / `else if` Anweisungen, die alle von ihnen mithilfe des gleichen Mechanismus als zueinander passende Klammern hervorgehoben werden konnte. Die <xref:Microsoft.VisualStudio.Package.Source> Basisklasse noch unterstützt, wie folgt: die Scanner muss den token Triggerwert zurückgeben <xref:Microsoft.VisualStudio.Package.TokenTriggers> zusammen mit den Triggerwert <xref:Microsoft.VisualStudio.Package.TokenTriggers> für das Token, die vor der Cursorposition eingefügt wird.  
  
 Weitere Informationen finden Sie unter [Klammer in einen Legacy-Sprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-colorization"></a>Analyse für die farbliche Kennzeichnung  
 Farbliche Kennzeichnung von Quellcode ist einfach, nur den Typ der token und return Farbinformationen zur dieses Typs zu identifizieren. Die <xref:Microsoft.VisualStudio.Package.Colorizer> -Klasse dient als Vermittler zwischen dem Editor und der Scanner Farbe Informationen über jedes Token bereitstellen. Die <xref:Microsoft.VisualStudio.Package.Colorizer> -Klasse verwendet die <xref:Microsoft.VisualStudio.Package.IScanner> Objekt in die farbliche Kennzeichnung von einer Zeile sowie zum Sammeln von Informationen zum Status für alle Zeilen in der Quelldatei. In die MPF-Language-Dienstklassen die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse muss keine außer Kraft gesetzt werden, da er mit dem Scanner kommuniziert nur über die <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle. Geben Sie das Objekt, implementiert die <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle durch Überschreiben der <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Methode für die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse.  
  
 Die <xref:Microsoft.VisualStudio.Package.IScanner> Scanner erhält eine Zeile des Quellcodes durch die <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> Methode. Aufrufe von der <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> Methode werden wiederholt, um das nächste Token in der Zeile zu erhalten, bis die Zeile des Tokens erschöpft ist. Für die farbliche Kennzeichnung behandelt das MPF alle Quellcode als Sequenz von Zeilen an. Aus diesem Grund muss der Scanner Quelle kommen Sie in Form von Linien bewältigen können. Darüber hinaus eine beliebige Zeile mit dem Scanner jederzeit übergeben werden kann, und ist nur garantiert, dass der Scanner die Statusvariable aus der Zeile vor der Zeile zu scannenden empfängt.  
  
 Die <xref:Microsoft.VisualStudio.Package.Colorizer> Klasse wird auch verwendet, um das token Auslöser zu identifizieren. Diese Trigger Teilen des verwalteten Paketframeworks mit, dass ein bestimmtes Token einen komplexeren Vorgang, z. B. wortvervollständigung initiieren kann oder zueinander passende Klammern. Da solche Trigger identifizieren schnell sein muss und muss mit einem beliebigen Speicherort vorkommen, ist der Scanner für diese Aufgabe am besten geeignet.  
  
 Weitere Informationen finden Sie unter [farbliche Kennzeichnung von Syntax in ein Legacy-Sprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-functionality-and-scope"></a>Analyse für Funktionen und Bereich  
 Funktionen und Umfang der Analyse erfordert mehr Aufwand als identifiziert nur die Typen von Token, die aufgetreten sind. Der Parser hat, um zu identifizieren, nicht nur den Typ des Tokens, sondern auch die Funktionen für die das Token verwendet wird. Angenommen, ein Bezeichner ist nur ein Name, aber in Ihrer Sprache ein Bezeichner ist möglicherweise der Name der Klasse, Namespace, Methode oder Variablen, je nach Kontext. Der allgemeine Typ des Tokens kann ein Bezeichner sein, aber die Bezeichner müssen auch eine andere Bedeutung, je nachdem, was ist und, in dem sie definiert ist. Diese Identifikation ist erforderlich, den Parser damit mehr umfassende Kenntnisse über die Sprache, die analysiert wird. Dies ist, wenn die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse eingeht. Die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse sammelt Informationen zu Bezeichnern, Methoden, übereinstimmende Sprachpaare (z. B. geschweifte Klammern und Klammern) und Language-Tripel (ähnlich wie Language-Paaren mit dem Unterschied, dass sind drei Schritte, z. B. "`foreach()`" "`{`"und"`}`"). Darüber hinaus können Sie überschreiben die <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse Kennung, unterstützt die in frühen Überprüfung der Breakpoints verwendet wird, damit der Debugger nicht geladen werden, und die **"Auto"** Debugfenster, die in lokalen dargestellt wird. Variablen und Parametern automatisch Wenn ein Programm gedebuggt wird und erfordert den Parser zur Identifizierung der entsprechenden lokalen Variablen und Parameter zusätzlich zu den, in dem der Debugger dargestellt.  
  
 Der <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt an den Parser übergeben wird, als Teil der <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt und eine neue <xref:Microsoft.VisualStudio.Package.AuthoringSink> Objekt erstellt jedes Mal, ein neues <xref:Microsoft.VisualStudio.Package.ParseRequest> Objekt wird erstellt. Darüber hinaus die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Methodenrückgabewert muss ein <xref:Microsoft.VisualStudio.Package.AuthoringScope> -Objekt, das verwendet wird, um verschiedene IntelliSense-Vorgänge zu behandeln. Die <xref:Microsoft.VisualStudio.Package.AuthoringScope> -Objekt verwaltet eine Liste der Deklarationen und eine Liste der Methoden, entweder die, je nach Ursache für die Analyse aufgefüllt wird. Die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse implementiert werden muss.  
  
## <a name="see-also"></a>Siehe auch  
 [Implementieren einen Sprachdienst Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Übersicht über die Legacy-Language-Dienst](../../extensibility/internals/legacy-language-service-overview.md)   
 [Farbliche Kennzeichnung von Syntax in ein Legacy-Sprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Zugehörige Klammer in einem Legacysprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

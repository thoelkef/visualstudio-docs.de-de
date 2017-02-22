---
title: "&#196;ltere Sprache Service – Grundlagen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Integration in Visual Studio-Sprachen"
  - "Language Services, Integration von Programmiersprachen"
  - "Visual Studio integrieren von Programmiersprachen"
  - "Programmiersprachen, Integration in Visual Studio"
ms.assetid: c15e0ccb-e7c5-4dbb-affb-fe3d3244debe
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# &#196;ltere Sprache Service – Grundlagen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Geben Sie einen Sprachdienst um eine Programmiersprache in Visual Studio integrieren. In diesem Thema erläutert die Funktionen, die in älteren Language Services verfügbar.  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Weitere Informationen über die neue Methode zum Implementieren eines Sprachdiensts finden Sie unter [\-Editor, und Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
 Ältere Sprache Services bieten die folgenden Funktionen:  
  
|Funktion|Beschreibung|  
|--------------|------------------|  
|Farben für Syntax|Bewirkt, dass die Editor\-Ansicht unterschiedliche Farben und Schriftarten für die verschiedenen Elemente einer Sprache angezeigt. Diese Unterscheidung kann erleichtern das Lesen und Bearbeiten von Dateien.<br /><br /> Weitere Informationen finden Sie unter [Syntaxfarben in eine Legacy\-Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).<br /><br /> Weitere Informationen zu dieser Funktion in verwalteten Paketframework \(MPF\), finden Sie unter [Farbliche Kennzeichnung von Syntax in einem Legacy\-Sprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).|  
|Anweisungsvervollständigung|Schließt eine Anweisung oder ein Schlüsselwort, das der Benutzer eingeben begonnen hat. Anweisungsabschluss hilft Benutzern, die schwer Anweisungen leichter, mit weniger Code eingeben und weniger wahrscheinlich Fehler eingeben.<br /><br /> Weitere Informationen finden Sie unter [Abschluss der Anweisung in eine Legacy\-Sprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).<br /><br /> Informationen zu diesem Feature die MPF finden Sie unter [Word\-Abschluss in einer Legacy\-Sprachdienst](../../extensibility/internals/word-completion-in-a-legacy-language-service.md).|  
|Zugehörige Klammer|Highlights kombiniert Zeichen wie z. B. geschweifte Klammern. Wenn der Benutzer gibt eine schließende Zeichen wie z. B. "}", Klammer hebt das entsprechende öffnende von Zeichen, wie z. B. "{". Wenn mehrere Ebenen von einschließenden Zeichen vorhanden sind, kann diese Funktion Benutzer bestätigen, dass die umschließenden Zeichen ordnungsgemäß miteinander kombiniert sind.<br /><br /> Informationen zu diesem Feature die MPF finden Sie unter [Zugehörige Klammer in einer Legacy\-Sprachdienst](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).|  
|Parameter Informationen QuickInfos|Zeigt eine Liste der möglichen Signaturen für die überladene Methode, die der Benutzer derzeit eingibt.<br /><br /> Weitere Informationen finden Sie unter [ParameterInfo in einer Legacy\-Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).<br /><br /> Informationen zu diesem Feature die MPF finden Sie unter [ParameterInfo in einer Legacy\-Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md).|  
|Fehler\-Marker|Zeigt eine rote Wellenlinie, auch bekannt als eine unterstrichene, unter dem Text, die syntaktisch falsch ist. Fehler\-Marker werden normalerweise verwendet, um Benutzer der falsch geschriebene Schlüsselwörter, nicht geschlossene Klammern, ungültige Zeichen und ähnliche Fehler aufmerksam zu machen.<br /><br /> In den Klassen MPF Fehler Marker erfolgt automatisch in die <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> Methode der <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasse.|  
  
 Viele dieser Funktionen erfordern den Sprachdienst Quellcode analysieren. Sie können häufig die Tokenisierung und Analysieren von Code für den Compiler oder Interpreter wiederverwenden.  
  
 Die folgenden Features beziehen sich auf Programmiersprachen unterstützt, jedoch sind nicht Teil des Language Services:  
  
|Funktion|Beschreibung|  
|--------------|------------------|  
|Ausdrucksauswertungen|Unterstützt die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger durch Überprüfen von Haltepunkten und einer Liste von Ausdrücken in angezeigt werden sollen die **Auto** Debug\-Fenster.<br /><br /> Weitere Informationen finden Sie unter [Language Service\-Unterstützung für das Debuggen](../../extensibility/internals/language-service-support-for-debugging.md).|  
|Tools zum Durchsuchen des Symbols|Unterstützt **Objektbrowser**, **Klassenansicht**, **Aufrufbrowser**, und **Ergebnisse der Symbolsuche**.|
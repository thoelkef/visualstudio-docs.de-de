---
title: "Word-Abschluss in einer Legacy-Sprachdienst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sprachdienste [Verwaltetes Paketframework], Wort vervollständigen von IntelliSense"
  - "IntelliSense, Wort vervollständigen"
  - "Wort vervollständigen"
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Word-Abschluss in einer Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wortvervollständigung gibt die fehlenden Zeichen auf teilweise eingegebenes Wort. Ist nur eine mögliche Abschluss, wird das Wort abgeschlossen, wenn der Abschluss Zeichen eingegeben wird. Wenn die partiellen Wörtern mehr als eine Möglichkeit übereinstimmt, wird eine Liste der mögliche Optionen angezeigt. Ein Abschluss\-Zeichen kann jedes Zeichen sein, das für Bezeichner verwendet wird.  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Um weitere Informationen finden Sie unter [Erweitern der\-Editor und Sprachdienste](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
## Implementierungsschritte  
  
1.  Wenn der Benutzer auswählt **Wort vervollständigen** aus der **IntelliSense** im Menü der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> an den Sprachdienst\-Befehl gesendet wird.  
  
2.  Die <xref:Microsoft.VisualStudio.Package.ViewFilter> Klasse fängt den Befehl aus und ruft die <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> \-Methode mit der Analyse Grund des <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3.  Die <xref:Microsoft.VisualStudio.Package.Source> \-Klasse dann Ruft die <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \-Methode zum Abrufen der Liste der möglichen Abschlüsse und zeigt dann die Wörter in einer QuickInfo mithilfe Auflisten der <xref:Microsoft.VisualStudio.Package.CompletionSet> Klasse.  
  
     Es ist nur eine übereinstimmendes Wort, die <xref:Microsoft.VisualStudio.Package.Source> \-Klasse abgeschlossen, wird das Wort.  
  
 Auch wenn der Scanner den Triggerwert zurückgibt <xref:Microsoft.VisualStudio.Package.TokenTriggers> Wenn das erste Zeichen eines Bezeichners eingegeben wird, der <xref:Microsoft.VisualStudio.Package.Source> \-Klasse erkennt dies und ruft die <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> \-Methode mit der Analyse Grund des <xref:Microsoft.VisualStudio.Package.ParseReason>. In diesem Fall muss der Parser erkennen, ob ein Element Auswahl Zeichen vorhanden, und geben Sie eine Liste von Elementen.  
  
## Aktivieren der Unterstützung für das vollständige Wort  
 Aktivieren der Unterstützung für Word Abschluss Satz der `CodeSense` benannte Parameter übergeben der <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Benutzerattribut das Sprachpaket zugeordnet. Dadurch wird die <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> Eigenschaft für die <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Klasse.  
  
 Der Parser muss eine Liste der Deklarationen als Antwort auf die Analyse Reason\-Wert zurückgeben <xref:Microsoft.VisualStudio.Package.ParseReason>, für die Word\-Vervollständigung ausgeführt werden.  
  
## Implementieren in der Methode ParseSource Wort vervollständigen  
 Für die Vervollständigung von Word die <xref:Microsoft.VisualStudio.Package.Source> \-Klasse ruft die <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> Methode für die <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasse, um eine Liste von möglichen Übereinstimmungen abzurufen. Sie müssen die Liste in einer Klasse, die von abgeleitet ist implementieren die <xref:Microsoft.VisualStudio.Package.Declarations> Klasse. Finden Sie unter der <xref:Microsoft.VisualStudio.Package.Declarations> \-Klasse auf die Methoden, die Sie implementieren müssen.  
  
 Wenn die Liste nur ein einzelnes Wort enthält die <xref:Microsoft.VisualStudio.Package.Source> \-Klasse fügt automatisch das Wort anstelle der partiellen Wörtern. Wenn die Liste mehr als ein Wort enthält die <xref:Microsoft.VisualStudio.Package.Source> \-Klasse stellt eine Tool Tipp Liste, aus der der Benutzer die entsprechende Option auswählen kann.  
  
 Betrachten Sie das Beispiel auch eine <xref:Microsoft.VisualStudio.Package.Declarations> Implementierung der Klasse in [Member\-Abschluss in einer Legacy\-Sprachdienst](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).
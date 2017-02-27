---
title: "Implementieren von Farben f&#252;r Syntax | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Syntax färben, Implementierung"
  - "Editoren [Visual Studio SDK] farbliche Kennzeichnung von text"
  - "Text, die farbliche Kennzeichnung in Editoren"
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Implementieren von Farben f&#252;r Syntax
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Der Sprachdienst Syntax farblich markiert gewährt, wird der Parser eine Textzeile in ein Array von Elementen färbbare konvertiert und Tokentypen, die diese färbbare Elementen zurückgegeben. Der Parser muss Tokentypen zurückgeben, die eine Liste der färbbare Elemente angehören.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zeigt jede färbbare Element im Codefenster gemäß den Attributen, die dem entsprechenden Tokentyp durch das Objekt zur farbdarstellung zugewiesen.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gibt eine Schnittstelle Parser und Parser\-Implementierung steht Ihnen völlig frei. Eine Standard\-Parser\-Implementierung wird jedoch in der Visual Studio\-Sprachpaket\-Projekt bereitgestellt. Für verwalteten Code bietet das Paketframework verwalteten \(MPF\) vollständige Unterstützung für die farbliche Kennzeichnung von Text.  
  
 Ältere Sprache Services werden als Teil eines VSPackage implementiert, aber der neuere Weg zum Implementieren von Language Service ist die Verwendung von MEF\-Erweiterungen. Weitere Informationen über die neue Methode zum Implementieren von Syntaxfarben finden Sie unter [Exemplarische Vorgehensweise: Markieren von Text](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor\-API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie die neue Editorfunktionen nutzen.  
  
## Schritte, gefolgt von einem Editor zum farbigen Anzeigen von Text  
  
1.  Der Editor Ruft die zur farbdarstellung durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> \-Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Objekt.  
  
2.  Ruft der Editor die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> Methode, um zu bestimmen, ob die zur farbdarstellung Zustand jeder Zeile außerhalb der zur farbdarstellung beibehalten werden soll.  
  
3.  Die zur farbdarstellung den Zustand, der außerhalb der zur farbdarstellung beibehalten werden benötigt, ruft der Editor die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> Methode zum Abrufen des Status der ersten Zeile.  
  
4.  Für jede Zeile im Puffer, ruft der Editor die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> \-Methode, die die folgenden Schritte ausführt:  
  
    1.  Scanner so konvertieren Sie den Text in Token wird die Zeile des Texts übergeben. Jedes Token gibt die token\-Text und den Typ des Tokens.  
  
    2.  Der Tokentyp wird in einen Index in einer Liste färbbare Elemente konvertiert.  
  
    3.  Die token Informationen werden verwendet, um in einem Array zu füllen, dass jedes Element des Arrays in ein Zeichen in der Zeile entspricht. Der im Array gespeicherten Werte sind die Indizes in der Liste färbbare Elemente.  
  
    4.  Für jede Zeile wird der Zustand am Ende der Zeile zurückgegeben.  
  
5.  Der zur farbdarstellung den Zustand beibehalten werden benötigt, speichert der Editor den Zustand für diese Zeile.  
  
6.  Der Editor stellt die Textzeile, die die zurückgegebenen Informationen aus der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode. Gehen Sie dazu folgendermaßen vor:  
  
    1.  Erhalten Sie für jedes Zeichen in der Zeile den Index färbbare Element.  
  
    2.  Wenn die Standardelemente der färbbare, Zugriff auf die färbbare Elementliste des Editors.  
  
    3.  Rufen Sie andernfalls des Sprachdiensts <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Methode, um ein färbbare Element abzurufen.  
  
    4.  Verwenden Sie die Informationen in das färbbare Element zum Rendern von Text in der Anzeige.  
  
## Verwaltete Paket Framework zur Farbdarstellung  
 Das verwaltete Package Framework \(MPF\) enthält alle Klassen, die zum Implementieren einer zur farbdarstellung erforderlich sind. Die Dienstklasse Sprache sollte erben die <xref:Microsoft.VisualStudio.Package.LanguageService> \-Klasse und die erforderlichen Methoden zu implementieren. Sie müssen einen Scanner und Parser angeben, durch die Implementierung der <xref:Microsoft.VisualStudio.Package.IScanner> \-Schnittstelle und eine Instanz dieser Schnittstelle aus Zurückgeben der <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Methode \(eine der Methoden, die in implementiert werden müssen die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse\). Weitere Informationen finden Sie unter [Farbliche Kennzeichnung von Syntax in einem Legacy\-Sprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## Siehe auch  
 [Gewusst wie: Verwenden von integrierten Färbbare Elemente](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Benutzerdefinierte Färbbare Elemente](../../extensibility/internals/custom-colorable-items.md)   
 [Entwickeln einer Sprache](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Farbliche Kennzeichnung von Syntax in einem Legacy\-Sprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
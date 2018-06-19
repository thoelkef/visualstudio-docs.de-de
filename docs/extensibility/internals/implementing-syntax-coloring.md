---
title: Implementieren von Syntaxfarben | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5502bd30378130e5977d427acb9df5b73226a05b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131854"
---
# <a name="implementing-syntax-coloring"></a>Implementieren die Farben für Syntax
Wenn der Sprachdienst syntaxhervorhebung bereitstellt, wird der Parser konvertiert eine Textzeile in ein Array von Elementen färbbare und Tokentypen entspricht diese färbbare Elemente zurückgegeben. Der Parser sollte Tokentypen zurückgeben, die auf eine Liste von färbbare Elemente gehören. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Zeigt jede färbbare Element im Codefenster nach den Attributen, die das Colorizer-Objekt dem entsprechenden Tokentyp zugewiesen.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gibt keine Parser-Schnittstelle, und die Parserimplementierung steht Ihnen völlig frei. Allerdings wird eine Standardimplementierung der Parser im Visual Studio-Sprachpaket Projekt bereitgestellt. Für verwalteten Code bietet des managed Package Framework (MPF) vollständige Unterstützung für die farbliche Kennzeichnung von Text an.  
  
 Dienste für Legacy-Sprachen werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Dienstfunktionen Sprache ist die Verwendung von MEF-Erweiterungen. Weitere Informationen über die neue Methode zum Implementieren von Syntaxfarben finden Sie unter [Exemplarische Vorgehensweise: Hervorheben von Text](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie beginnen, den neuen Editor API so bald wie möglich verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Schritte, gefolgt von einer zur farblichen Kennzeichnung der Text-Editor  
  
1.  Der Editor Ruft die Colorizer durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Objekt.  
  
2.  Der Editor Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> Methode, um zu bestimmen, ob die Colorizer Zustand jeder Zeile außerhalb der Colorizer beibehalten werden soll.  
  
3.  Wenn die Colorizer die außerhalb der Colorizer beibehalten werden muss, ruft der Editor die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> Methode, um den Zustand der ersten Zeile abzurufen.  
  
4.  Für jede Zeile im Puffer, ruft der Editor die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> -Methode, die die folgenden Schritte ausführt:  
  
    1.  Die Textzeile an einen Scanner zum Konvertieren von Text in Token übergeben wird. Jedes Token gibt die token-Text und der Typ des Sicherheitstokens.  
  
    2.  Der Tokentyp wird in einen Index in einer färbbare Elementliste konvertiert.  
  
    3.  Das token Informationen werden verwendet, um in einem Array zu füllen, dass jedes Element des Arrays in ein Zeichen in der Zeile entspricht. Die im Array gespeicherten Werte werden die Indizes in der Liste der färbbare Elemente.  
  
    4.  Der Status am Ende der Zeile wird für jede Zeile zurückgegeben.  
  
5.  Wenn die Colorizer die beibehalten werden muss, wird der Editor den Status für diese Zeile zwischengespeichert.  
  
6.  Der Editor rendert die Textzeile, die die zurückgegebenen Informationen aus der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode. Gehen Sie dazu folgendermaßen vor:  
  
    1.  Erhalten Sie für jedes Zeichen in der Zeile den Index färbbare Element.  
  
    2.  Wenn Sie die färbbare Standardelemente verwenden möchten, Zugriff auf die färbbare Elementliste des Editors.  
  
    3.  Rufen Sie andernfalls die Sprachdienst <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Methode, um eine färbbare Element abzurufen.  
  
    4.  Verwenden Sie die Informationen in das färbbare Element mit der Text in der Anzeige gerendert.  
  
## <a name="managed-package-framework-colorizer"></a>Managed Package Framework Colorizer  
 Des managed Package Framework (MPF) stellt alle Klassen, die zum Implementieren einer Colorizer erforderlich sind. Die Language-Dienstklasse sollte erben die <xref:Microsoft.VisualStudio.Package.LanguageService> -Klasse und die erforderlichen Methoden zu implementieren. Müssen Sie einen Scanner und Parser angeben, durch die Implementierung der <xref:Microsoft.VisualStudio.Package.IScanner> Schnittstelle, und eine Instanz dieser Schnittstelle von Zurückgeben der <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Methode (eine der Methoden, die in implementiert werden müssen, die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse). Weitere Informationen finden Sie unter [farbliche Kennzeichnung von Syntax in ein Legacy-Sprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Verwenden von integrierten Färbbare Elemente](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Benutzerdefinierte Färbbare Elemente](../../extensibility/internals/custom-colorable-items.md)   
 [Entwickeln von einem Legacy-Sprachdienst](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
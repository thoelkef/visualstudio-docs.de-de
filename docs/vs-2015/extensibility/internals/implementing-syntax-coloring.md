---
title: Implementieren von Syntaxfarben | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a4315b9e6b6fdb12a0fcb3e97f6b208d6b84acd9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259249"
---
# <a name="implementing-syntax-coloring"></a>Implementieren von Syntaxfarben
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn der Sprachdienst die farbliche Markierung der Syntax bereitstellt, wird der Parser konvertiert eine Textzeile in ein Array der kolorierbaren Elemente, und gibt die Typen von Sicherheitstoken für diese kolorierbaren Elemente zurück. Der Parser sollte Tokentypen zurückgeben, die eine Liste der kolorierbaren Elemente angehören. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Zeigt jede kolorierbaren Elements im Code-Fenster gemäß der Attribute, die von der Farbauswahl-Objekt zugeordnet wird, dem entsprechenden Tokentyp an.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gibt keine Parser-Schnittstelle, und der Parser-Implementierung steht Ihnen völlig frei. Allerdings wird eine Standardimplementierung der Parser in das Sprachpaket für Visual Studio-Projekt bereitgestellt. Für verwalteten Code bietet das managed Package Framework (MPF) vollständige Unterstützung für die farbliche Kennzeichnung von Text an.  
  
 Legacy-Sprachdienste werden als Teil eines VSPackage implementiert, aber die neuere Methode zum Implementieren von Sprache-Service-Features ist die Verwendung von MEF-Erweiterungen. Weitere Informationen zu die neue Methode zum Implementieren von Syntaxfarben finden Sie unter [Exemplarische Vorgehensweise: Hervorheben von Text](../../extensibility/walkthrough-highlighting-text.md).  
  
> [!NOTE]
>  Es wird empfohlen, dass Sie nun den neuen Editor API so bald wie möglich zu verwenden. Dies verbessert die Leistung des Sprachdiensts und können Sie neue Features im Editor nutzen.  
  
## <a name="steps-followed-by-an-editor-to-colorize-text"></a>Schritte, gefolgt von einem Editor zum farbigen Anzeigen von Text  
  
1.  Der Editor Ruft die Farbauswahl durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Objekt.  
  
2.  Der Editor Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> Methode, um zu bestimmen, ob die Farbauswahl Zustand jeder Zeile außerhalb der Farbauswahl beibehalten werden soll.  
  
3.  Die Farbauswahl den Status außerhalb der Farbauswahl beibehalten werden benötigt, ruft der Editor die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> Methode, um den Zustand der ersten Zeile abzurufen.  
  
4.  Für jede Zeile im Puffer, ruft der Editor die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> -Methode, die die folgenden Schritte ausführt:  
  
    1.  Die Zeile des Texts wird an einen Scanner so konvertieren Sie den Text in Token übergeben. Jedes Token gibt an, die token-Text und der Typ des Sicherheitstokens.  
  
    2.  Der Tokentyp wird in einen Index in eine Liste der kolorierbaren Elemente konvertiert.  
  
    3.  Die token Informationen werden verwendet, um in einem Array zu füllen, sodass jedes Element des Arrays in ein Zeichen in der Zeile entspricht. Die Werte im Array gespeichert sind, die Indizes in der Liste der kolorierbaren Elemente.  
  
    4.  Für jede Zeile wird der Zustand am Ende der Zeile zurückgegeben.  
  
5.  Wenn die Farbauswahl den Zustand verwaltet werden, erforderlich sind, werden der Editor den Zustand für diese Zeile zwischengespeichert.  
  
6.  Der Editor rendert die Textzeile, die mit den Informationen zurückgegeben, die von der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode. Gehen Sie dazu folgendermaßen vor:  
  
    1.  Erhalten Sie für jedes Zeichen in der Zeile den Index des kolorierbaren Elements.  
  
    2.  Wenn Sie die standardmäßige kolorierbaren Elemente verwenden zu können, Zugriff auf der Editorliste kolorierbaren Elemente.  
  
    3.  Rufen Sie andernfalls des Sprachdiensts <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> Methode, um ein färbbares Element abzurufen.  
  
    4.  Verwenden Sie die Informationen in das kolorierbare Element, mit der Text in der Anzeige gerendert.  
  
## <a name="managed-package-framework-colorizer"></a>Managed Package Framework Farbauswahl  
 Das managed Package Framework (MPF) stellt alle Klassen, die erforderlich sind, um eine Farbauswahl zu implementieren. Sprachdienstklasse sollten erben die <xref:Microsoft.VisualStudio.Package.LanguageService> -Klasse und die erforderlichen Methoden zu implementieren. Sie müssen einen Scanner und Parser angeben, durch die Implementierung der <xref:Microsoft.VisualStudio.Package.IScanner> -Schnittstelle und eine Instanz dieser Schnittstelle vom Zurückgeben der <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> Methode (eine der Methoden, die in implementiert werden müssen die <xref:Microsoft.VisualStudio.Package.LanguageService> Klasse). Weitere Informationen finden Sie unter [einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Verwenden Sie die integrierten kolorierbaren Elemente](../../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Benutzerdefinierte kolorierbare Elemente](../../extensibility/internals/custom-colorable-items.md)   
 [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Einfärben der Syntax in einem Legacysprachdienst](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)


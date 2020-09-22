---
title: Syntax Farbgebung in benutzerdefinierten Editoren | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a0233873ba5d6ea2fca746f8e12f4bf693b79da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841146"
---
# <a name="syntax-coloring-in-custom-editors"></a>Syntaxfarben in benutzerdefinierten Editoren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio-Umgebungs-SDK-Editoren, einschließlich des Kern-Editors, verwenden Sprachdienste, um bestimmte syntaktische Elemente zu identifizieren und diese mit den angegebenen Farben für eine bestimmte Dokument Ansicht anzuzeigen.  
  
## <a name="colorization-requirements"></a>Farbige Anforderungen  
 Alle Editoren, die die Farbgebung eines sprach Dienstanbieter implementieren, müssen:  
  
1. Verwenden Sie ein Objekt <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> , das implementiert, um den Text für die Farbgebung zu verwalten, und ein Objekt, das implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> , um eine Dokument Ansicht des Texts bereitzustellen.  
  
2. Rufen Sie eine Schnittstelle zu einem bestimmten Sprachdienst ab, indem Sie den Dienstanbieter des VSPackages mithilfe der identifizierenden GUID des sprach Dienstanbieters Abfragen.  
  
3. Ruft die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> Methode des-Objekts auf, das implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> . Diese Methode ordnet den Sprachdienst der- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Implementierung zu, die das VSPackage verwendet, um den Text zu verwalten, der farbig markiert werden soll.  
  
## <a name="core-editor-usage-of-a-language-services-colorizer"></a>Basis-Editor-Verwendung der Farbgebung eines sprach Dienstanbieter  
 Wenn ein Sprachdienst mit einer Farbauswahl von einer Instanz des Kern-Editors abgerufen wird, werden die Text-und Renderingvorgänge durch die Farbgebung eines sprach Dienstanbieter automatisch durchgeführt, ohne dass ein weiterer Eingriff erforderlich ist.  
  
 Die IDE ist transparent:  
  
- Ruft die Farbgebung bei Bedarf auf, um Text beim Hinzufügen oder ändern in der Implementierung von zu analysieren und zu analysieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> .  
  
- Stellt sicher, dass die von der-Implementierung bereitgestellte Dokument Ansicht <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> mithilfe der von der Farbgebung zurückgegebenen Informationen aktualisiert und neu gezeichnet wird.  
  
## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>Nicht-Kern-Editor-Verwendung der Farbgebung eines sprach Dienstanbieter  
 Nicht-Kern-Editor-Instanzen können auch den Syntax Farb Erfassungs Dienst eines sprach Dienstanbieter verwenden. Sie müssen jedoch explizit die Farbgebung des dienstanwenders abrufen und anwenden und die Dokument Sichten selbst neu zeichnen.  
  
 Hierfür ist ein nicht-Kern-Editor für Folgendes erforderlich:  
  
1. Abrufen des Farb Erfassers Objekts eines sprach dienstanders (das `T:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer` und implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2> ). Das VSPackage bewirkt dies durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> -Methode für die-Schnittstelle des sprach Dienstanbieter.  
  
2. Ruft die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode auf, um anzufordern, dass ein bestimmter Textabschnitt farbig markiert werden soll.  
  
     Die- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> Methode gibt ein Array von-Werten zurück, eines für jeden Buchstaben in der Text Spanne, die farbig markiert wird. Außerdem wird der Textabschnitt als eine bestimmte Art von Kolon-Element, z. b. ein Kommentar, ein Schlüsselwort oder ein Datentyp, identifiziert.  
  
3. Verwenden Sie die von zurückgegebenen farbliche Informationen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> , um den Text neu zu zeichnen und anzuzeigen.  
  
> [!NOTE]
> Zusätzlich zur Verwendung der Farbgebung eines sprach Dienstanbieter kann ein VSPackage auswählen, dass der Text Farb Mechanismus für das allgemeine Visual Studio-Umgebungs-SDK verwendet werden soll. Weitere Informationen zu diesem Mechanismus finden Sie unter [Verwenden von Schriftarten und Farben](../extensibility/using-fonts-and-colors.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Syntax Farbgebung in einem Legacy Sprachdienst](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementieren von Syntax Farben](../extensibility/internals/implementing-syntax-coloring.md)   
 [Gewusst wie: Verwenden integrierter, Färb baren Elemente](../extensibility/internals/how-to-use-built-in-colorable-items.md)   
 [Benutzerdefinierte einfärbbare Elemente](../extensibility/internals/custom-colorable-items.md)

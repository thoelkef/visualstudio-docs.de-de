---
title: "Ältere Sprache Dienstschnittstellen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 925b504d8cba4813631d4f8ba6f7dbd9750f5eae
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="legacy-language-service-interfaces"></a>Legacy-Sprachdienst-Schnittstellen
Für eine bestimmte Programmiersprache können nur eine Instanz eines Sprachdiensts zu einem Zeitpunkt vorhanden sein. Allerdings kann ein Dienst (einsprachig) mehr als einer der Redakteure dienen.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]einen Sprachdienst ist nicht mit einem bestimmten Editor zuordnen werden. Wenn Sie einen Dienstvorgang Sprache anfordern, müssen Sie die geeigneten Editor als Parameter identifizieren.  
  
## <a name="common-interfaces-associated-with-language-services"></a>Common Language Diensten zugeordnet Schnittstellen  
 Der Editor ruft Ihre Sprachdienst durch Aufrufen von <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> für das entsprechende VSPackage. Der Dienst-ID (SID) in diesem Aufruf übergebenen identifiziert der Sprachdienst angefordert wird.  
  
 Sie können die Dienstschnittstellen Core Sprache auf eine beliebige Anzahl von separaten Klassen implementieren. Allerdings ist eine gängige Methode in einer einzelnen Klasse die folgenden Schnittstellen implementieren:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (optional)  
  
 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> -Schnittstelle muss implementiert werden, auf die Dienste für alle Sprachen. Es enthält Informationen zu Ihrem Sprachdienst, z. B. den lokalisierten Namen der Sprache, die die Dateinamenerweiterungen der Sprachdienst und zum Abrufen einer Colorizer zugeordnet.  
  
## <a name="additional-language-service-interfaces"></a>Zusätzliche Sprachdienst-Schnittstellen  
 Andere Schnittstellen können mit dem Language-Dienst bereitgestellt werden. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fordert eine separate Instanz dieser Schnittstellen für jede Instanz des Textpuffers. Aus diesem Grund sollten Sie jede dieser Schnittstellen in sein eigenes Objekt implementieren. Die folgende Tabelle zeigt die Schnittstellen, die eine Instanz pro Instanz des Text-Puffer erforderlich.  
  
|Schnittstelle|Beschreibung|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Verwaltet die Code-Fenster Zusatzelemente, z. B. die Dropdown-Leiste. Sie können diese Schnittstelle abrufen, indem Sie mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Methode. Es ist eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> pro Fenster "Code".|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Färbt Programmiersprachen-Schlüsselworten und Trennzeichen. Sie können diese Schnittstelle abrufen, indem Sie mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Methode. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>Paint Zeitpunkt aufgerufen wird. Vermeiden Sie rechenintensive Aufgaben innerhalb <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> oder konnte die Leistung darunter leiden.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Zeigt QuickInfos für IntelliSense-Parameter. Wenn der Sprachdienst erkennt, muss ein Zeichen, das diese Methodendaten an angezeigt, z. B. eine öffnende Klammer, ruft er die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> -Methode benachrichtigen Sie den Text anzuzeigen, die der Sprachdienst ist für die Anzeige einer Parameter-QuickInfo bereit. Textansicht ruft dann wieder in der Sprachdienst nach mit den Methoden der der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> Schnittstelle, um die erforderlichen Informationen für die Anzeige der QuickInfo abzurufen.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Stellt IntelliSense-Anweisungsvervollständigung bereit. Wenn der Sprachdienst eine Vervollständigungsliste anzeigen bereit ist, ruft er die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode für die Textansicht. Textansicht ruft dann wieder in der Sprachdienst nach verwenden Sie Methoden für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> Objekt.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Ermöglicht die Änderung der Textansicht Befehlshandler verwenden. Die Klasse, in dem Sie implementieren, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Schnittstelle muss auch implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle. Textansicht Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Objekt durch Abfragen der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> -Objekt, das übergeben wird die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Methode. Ein SqlEndAltersStep vorhanden sein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Objekt für jede Ansicht.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Fängt Befehle, dass der Benutzer in das Codefenster Typen ab. Überwachen Sie die Ausgabe der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Implementierung zur Bereitstellung von Informationen über den benutzerdefinierten Abschluss und Änderung anzeigen<br /><br /> Übergabe Ihrer <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Objekt, das die Textansicht Aufruf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von einem Legacy-Sprachdienst](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Prüfliste: Erstellen eines Legacysprachdiensts](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
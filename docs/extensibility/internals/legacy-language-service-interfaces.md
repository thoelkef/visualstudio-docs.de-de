---
title: "&#196;ltere Sprache-Schnittstellen | Microsoft Docs"
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
  - "IVsLanguageInfo-Schnittstelle"
  - "Language Services, Objekte"
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# &#196;ltere Sprache-Schnittstellen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Für jede bestimmte Programmiersprache kann es nur eine Instanz des Sprachdiensts gleichzeitig vorhanden sein.  Allerdings kann ein einsprachiger Dienst mehr als einen Editor dienen.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ordnet einen Sprachdienst keinem bestimmten Editor.  Wenn Sie einen Sprachen dienstvorgang benötigen, müssen Sie den geeigneten Editor als Parameter angeben.  
  
## Allgemeine Sprachendiensten zugeordnete Schnittstellen  
 Im Editor wird der Sprachdienst ab, indem er <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> auf entsprechenden VSPackage aufruft.  Die Dienst ID \(SID\) in diesem Aufruf wird der Sprachdienst, die angefordert wird.  
  
 Sie können die wichtigsten Schnittstellen Sprachdienst auf einer beliebigen Anzahl von anderen Klassen implementiert werden.  Es ist ein allgemeiner Ansatz, die folgenden Schnittstellen in einer einzelnen Klasse zu implementieren:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> \(optional\)  
  
 Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>\-Schnittstelle muss auf allen Sprachendiensten implementiert werden.  Es stellt Informationen über den Sprachdienst, z. B. den lokalisierten Namen der Sprache, die Dateinamenerweiterungen, die mit dem Sprachdienst zugeordnet werden und wie eine farbige Darstellung veranschaulicht.  
  
## Weitere Sprachendienst\-Schnittstellen  
 Andere Schnittstellen können mit dem Sprachdienst bereitgestellt werden.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] erfordert eine separate Instanz dieser Schnittstellen für jede Instanz des Textpuffers.  Daher sollten Sie jede dieser Schnittstellen on Its Own Objekt implementieren.  In der folgenden Tabelle werden die Schnittstellen, die eine Instanz pro Textpuffer Objektinstanz erforderlich sind.  
  
|Schnittstelle|Beschreibung|  
|-------------------|------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Verwaltet Codefenster zusatzelemente, wie die Dropdownliste Leiste.  Sie können diese Schnittstelle abrufen, indem Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>\-Methode verwenden.  Es gibt ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> pro Codefenster.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Farbig stellt Schlüsselwörter und Trennzeichen dar.  Sie können diese Schnittstelle abrufen, indem Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>\-Methode verwenden.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> wird an der Farben Zeit bezeichnet.  Vermeiden Sie Berechnung\-intensive Arbeit innerhalb <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> kann die Leistung oder leiden.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Stellt IntelliSense\-Parameter die QuickInfo bereit.  Wenn der Sprachdienst erkennt, wird ein Zeichen, das angibt, dass Daten Methoden, z. B. eine öffnende Klammer angezeigt werden sollen, es, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>\-Methode auf, um die Textansicht zu benachrichtigen, dass der Sprachdienst bereit ist, eine Parameterinformationens\-QuickInfo anzuzeigen.  Die Aufrufe der Textansicht dann wieder in den Sprachdienst mithilfe der Methoden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>\-Schnittstelle, um die erforderlichen Informationen zu erhalten, um die QuickInfo anzuzeigen.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Stellt IntelliSense\-Anweisungsvervollständigung bereit.  Wenn der Sprachdienst bereit ist, eine Vervollständigungsliste anzuzeigen, ruft sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>\-Methode für die Textansicht an.  Die Aufrufe der Textansicht dann wieder in den Sprachdienst mithilfe von Methoden für den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>\-Objekt.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Ermöglicht das Ändern der Textansicht mithilfe des Befehls handlers.  Die Klasse, in der die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>\-Schnittstelle implementieren, muss auch die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\-Schnittstelle implementieren.  Die Textansicht ruft das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>\-Objekt ab, indem er das <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\-Objekt abgefragt wird, das in die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>\-Methode übergeben wird.  Es sollte ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>\-Objekt für jede Sicht sein.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Fängt diese Befehle der Benutzer auf die im Codefenster ab.  Überwachen Sie die Ausgabe der <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Informationen zum Schließen, um eine benutzerdefinierte Implementierung und Änderung der Ansicht bereitzustellen<br /><br /> Um das <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\-Objekt der Textansicht übergeben, Aufrufs <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>.|  
  
## Siehe auch  
 [Entwickeln einer Sprache](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Prüfliste: Erstellen einer Legacy\-Sprachdienst](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
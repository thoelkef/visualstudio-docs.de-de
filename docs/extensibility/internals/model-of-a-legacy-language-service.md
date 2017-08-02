---
title: "Modell eines Legacy-Language-Diensts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Language Services, Modell"
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Modell eines Legacy-Language-Diensts
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Sprachdienst definiert die Elemente und Funktionen für eine bestimmte Sprache und wird verwendet, um den Editor mit spezifischen Informationen zu dieser Sprache bereitzustellen.  Beispielsweise muss der Editor den Elementen und Schlüsselwörter der Sprache kennen, um Syntaxfarbe zu unterstützen.  
  
 Der Sprachdienst arbeitet eng mit dem Textpuffer, der vom Editor, und die Ansicht, die verwaltete den Editor enthält.  Die Option Microsoft IntelliSense **QuickInfo** ist ein Beispiel für eine Funktion, die einen Sprachdienst bereitgestellt wird.  
  
## Ein minimaler Sprachdienst  
 Die grundlegendste Sprachdienst enthält die beiden folgenden Objekte:  
  
-   Der *Sprachdienst* implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>\-Schnittstelle.  Ein Sprachdienst enthält Informationen zu der Sprache, einschließlich seines Namens, Dateinamenerweiterungen, Code und fenster\-manager farbige Darstellung.  
  
-   Die *farbige Darstellung* implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>\-Schnittstelle.  
  
 Die folgende konzeptionelle Zeichnung zeigt ein Modell eines grundlegenden Sprachdiensts an.  
  
 ![Grafik zum Sprachdienstmodell](~/extensibility/media/vslanguageservicemodel.gif "vsLanguageServiceModel")  
Grundlegendes Sprachdienst Modells  
  
 Die Dokumentfenster hostet die *Ansicht* des Editors *Dokumente* in diesem Fall der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kern des Editors.  Die Dokumente und der Textpuffer werden durch den Besitz Editor.  Diese Objekte funktionieren mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] durch ein spezialisiertes Dokumentfenster, das ein *Codefenster*aufgerufen wird.  Das Codefenster wird in einem <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>\-Objekt, das von der IDE erstellt und verwaltet wird.  
  
 Wenn eine Datei mit einer angegebenen Erweiterung geladen wird, sucht der Editor den Sprachdienst, der mit dieser Erweiterung zugeordnet ist, und übergibt ihr das Codefenster, indem er die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>\-Methode aufgerufen wird.  Der Sprachdienst gibt einen *Code fenster\-manager*zurück, der die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>\-Schnittstelle implementiert.  
  
 Die folgende Tabelle enthält eine Übersicht über die Objekte im Modell.  
  
|Komponente|Objekt|Funktion|  
|----------------|------------|--------------|  
|Textpuffer|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Ein Unicode\-Lese\-\/Schreibzugriff\-Textstream.  Es ist möglich, Text für andere Codierungen verwendet werden soll.|  
|Codefenster|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Ein Dokumentfenster mit einem oder mehreren Textansichten enthält.  Wenn der Modus [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] MDI \(Multiple Document Interface\) ist, wird das Codefenster ein untergeordnetes MDI\-Element.|  
|Textansicht|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Ein Fenster, in dem der Benutzer navigiert und Text anzeigen können, indem die Tastatur als auch die Maus verwenden.  Eine Textansicht als Editor für den Benutzer angezeigt wird.  Sie können Textansichten in gewöhnlichen Editorfenster, in das Fenster Ausgabe und das Direktfenster verwenden.  Außerdem können Sie einem oder mehreren Textansichten in einem Fenster Code konfigurieren.|  
|Text Manager|Verwaltet durch den <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> Dienst, aus dem Sie ein Zeiger abgerufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>|Eine Komponente, die die allgemeine Informationen beibehält, die von allen Komponenten gemeinsam genutzt werden, die zuvor beschrieben werden.|  
|Sprachdienst|Implementierungen abhängiges Element. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>implementiert|Ein Objekt, das den Editor mit sprachspezifischer Informationen wie Anweisungsvervollständigung und erhält, Syntax\-Hervorhebung stützen Übereinstimmungen ab.|  
  
## Siehe auch  
 [Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren](../../extensibility/document-data-and-document-view-in-custom-editors.md)
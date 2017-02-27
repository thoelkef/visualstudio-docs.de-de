---
title: "Enthaltene Sprachen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK] legacy - enthaltenen Sprachen"
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# Enthaltene Sprachen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Eingeschlossene Sprachen* sind Sprachen, die von anderen Sprachen enthalten sind.  Zum Beispiel kann HTML in den vstecasp\-Seiten [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Skripts.  Eine Dual LANGUAGE\-Architektur ist erforderlich, damit der ASPX\-Datei\-Editor Bearbeiten, IntelliSense Farbauftrag und andere Features für das HTML und die Skriptsprache zur Verfügung stellt.  
  
## Implementierung  
 Die wichtigste Schnittstelle, die für enthaltene Sprachen implementieren müssen, ist die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>\-Schnittstelle.  Diese Schnittstelle wird von jeder Sprache implementiert, die in einer primären Sprache aufgenommen werden kann.  Er gibt Zugriff auf die farbigen Darstellung des Sprachdiensts, die auf den Text zur primären Filter und Sprachdienst ID.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> ermöglicht es Ihnen, eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>\-Schnittstelle zu erstellen.  In den folgenden Schritten wird erläutert, wie eine eingeschlossene Code implementiert:  
  
1.  Verwenden Sie `QueryService()` , um die Sprachdienst ID und die Schnittstellen\-ID <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>abzurufen.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A>\-Methode auf, um eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>\-Schnittstelle zu erstellen.  Führen Sie eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>\-Schnittstelle, eine Element\-ID aus <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>\(eine oder mehrere <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>aus, oder <xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>\) und eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>\-Schnittstelle.  
  
3.  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>\-Schnittstelle, die das Objekt puffer\-Koordinator Text ist, stellt die Basisdienste, die erforderlich sind, um Positionen in einer Grunddatei in den sekundären Puffer der Sprache zuzuordnen.  
  
     Beispielsweise kann in einer ASPX\-Datei enthält die Grunddatei das ASP.NET, HTML und den gesamten Code enthalten ist.  Es schließt der sekundären Puffer, nur den enthaltenen Code, zusammen mit allen Klassendefinitionen, um den sekundären Puffer eine gültige Codedatei zu erstellen.  Der Puffer koordinator behandelt die Arbeit des Koordinierens von Bearbeitungen aus einem Puffer in den anderen.  
  
4.  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>\-Methode, die die primäre Sprache ist, teilt dem Puffer koordinator mit, welcher Text innerhalb des Puffers zum entsprechenden Text in einen sekundären Puffer zugeordnet ist.  
  
     Die Sprache übergibt ein Array der <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> Struktur, die derzeit nur eine primäre und sekundäre Spanne enthält.  
  
5.  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A>\-Methode und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A>\-Methode stellen die Zuordnung von primärem auf den sekundären Puffer und umgekehrt.
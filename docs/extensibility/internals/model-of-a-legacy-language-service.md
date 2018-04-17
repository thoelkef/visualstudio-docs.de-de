---
title: Modell von einem Legacy-Sprachdienst | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 943f0f013045e3082af3069ed4d45aaed1096869
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="model-of-a-legacy-language-service"></a>Modell von einem Legacy-Sprachdienst
Ein Sprachdienst definiert die Elemente und Funktionen für eine bestimmte Sprache und verwendet, um den Editor durch spezifische Informationen zum jeweiligen Sprache bereitzustellen. Beispielsweise muss der Editor die Elemente und die Schlüsselwörter der Sprache kennen, um Farben für Syntax zu unterstützen.  
  
 Der Sprachdienst arbeitet eng mit der Verwaltung der Editor und die Ansicht, die der Editor enthält Textpuffer. Microsoft IntelliSense **Quick Info** Option ist ein Beispiel für eine Funktion, die von einem Sprachdienst bereitgestellt.  
  
## <a name="a-minimal-language-service"></a>Eine minimale-Sprachdienst  
 Die meisten grundlegenden Sprachdiensts enthält die folgenden zwei Objekte:  
  
-   Die *Sprachdienst* implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle. Ein Sprachdienst verfügt über die Sprache, einschließlich Name, Dateinamenerweiterungen, Fenstermanager-Code und Colorizer.  
  
-   Die *Colorizer* implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Schnittstelle.  
  
 In der folgende konzeptionelle Zeichnung zeigt ein Modell eines grundlegenden Language-Diensts.  
  
 ![Sprachdienstmodell](../../extensibility/media/vslanguageservicemodel.gif "VsLanguageServiceModel")  
Grundlegende Service Sprachmodell  
  
 Das Dokument Fenster hostet die *Dokumentansicht* des Editors, in diesem Fall die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Core-Editor. Vom Editor gehören die Dokumentansicht und den Textpuffer. Diese Objekte funktionieren mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] durch einem speziellen Dokumentfenster aufgerufen, eine *Fenster "Code"*. Das Codefenster befindet sich einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> -Objekt, das erstellt und von der IDE gesteuert wird.  
  
 Beim Laden einer Datei mit einer bestimmten Erweiterung Editor sucht der Sprachdienst Erweiterung zugeordnet und übergibt ihm das Codefenster durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Methode. Die Language-Dienst gibt eine *Code Fenstermanager*, implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> Schnittstelle.  
  
 Die folgende Tabelle enthält eine Übersicht über die Objekte im Modell.  
  
|Komponente|Object|Funktion|  
|---------------|------------|--------------|  
|Textpuffer|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Eine Unicode-Lese-Schreib-Textdatenstrom. Es ist möglich, für den Text auf andere Codierungen verwenden.|  
|Codefenster|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Ein Dokumentfenster, das eine oder mehrere Textansichten enthält. Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird im Modus Multiple Document Interface (MDI), ist das Codefenster untergeordnetes MDI-Fenster.|  
|Textansicht|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Ein Fenster, in dem der Benutzer navigieren und Anzeigen von Text mithilfe der Tastatur und Maus. Eine Textansicht wird dem Benutzer als Editor angezeigt. Sie können Textansichten in normalen-Editor-Fenster, Fenster "Ausgabe" und das "Direktfenster" verwenden. Darüber hinaus können Sie eine oder mehrere Textansichten in einem Fenster des Code konfigurieren.|  
|Text-manager|Von verwaltet die <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> Dienst, die Sie erhalten eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> Zeiger|Eine Komponente, die allgemeine Informationen, die alle Komponenten, die zuvor beschriebenen freigegebenen verwaltet.|  
|-Sprachdienst|Implementierungsabhängig; implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Ein Objekt, das sprachspezifische Informationen wie syntaxhervorhebung, Anweisungsvervollständigung und Klammer den Editor bietet.|  
  
## <a name="see-also"></a>Siehe auch  
 [Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren](../../extensibility/document-data-and-document-view-in-custom-editors.md)
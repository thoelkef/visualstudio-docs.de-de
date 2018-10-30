---
title: Modell eines Legacysprachdiensts | Microsoft-Dokumentation
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
ms.openlocfilehash: 381c5b37cdc5d8a166003bdf7dd931dd95e6dcb3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49943088"
---
# <a name="model-of-a-legacy-language-service"></a>Modell eines Legacysprachdiensts
Ein Sprachdienst definiert die Elemente und Funktionen für eine bestimmte Sprache und wird verwendet, um den Editor Informationen, die speziell für diese Sprache bereitzustellen. Beispielsweise muss der Editor die Elemente und Schlüsselwörter der Sprache kennen, um Farben für Syntax zu unterstützen.  
  
 Der Sprachdienst arbeitet eng mit dem Textpuffer, die von der Editor und die Ansicht, die den Editor enthält verwaltet werden. Die Microsoft IntelliSense **Quick Info** Option ist ein Beispiel für eine Funktion, die von einem Sprachdienst bereitgestellt.  
  
## <a name="a-minimal-language-service"></a>Ein Minimal-Sprachdienst  
 Die meisten grundlegenden Sprachdiensts enthält die folgenden zwei Objekte:  
  
- Die *Sprachdienst* implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle. Ein Sprachdienst hat Informationen zu Sprache, einschließlich der Namen, die Dateinamenerweiterungen Weitere Erweiterungen, die Codefenster-Manager und die Farbauswahl.  
  
- Die *Farbauswahl* implementiert die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Schnittstelle.  
  
  Die folgende schematische Darstellung zeigt ein Modell eines einfachen Sprachdiensts.  
  
  ![Sprachdienstmodell](../../extensibility/media/vslanguageservicemodel.gif "VsLanguageServiceModel")  
  Grundlegende sprachendienstmodell  
  
  Die Dokument-Fenster-Hosts die *Dokumentansicht* des Editors in diesem Fall die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Kern-Editor. Die Ansicht des Dokuments und dem Textpuffer gehören durch den Editor. Diese Objekte funktionieren mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] durch einem speziellen Fenster aufgerufen, eine *Codefenster*. Im Code-Fenster befindet sich einem <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> -Objekt, das erstellt und von der IDE gesteuert.  
  
  Wenn eine Datei mit einer bestimmten Erweiterung geladen wird, wird der Editor sucht den Sprachdienst, der dieser Erweiterung zugeordnet und übergibt, Code-Fenster durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Methode. Der Language-Dienst gibt eine *codefenstermanager*, implementiert der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> Schnittstelle.  
  
  Die folgende Tabelle enthält eine Übersicht über die Objekte im Modell.  
  
| Komponente | Object | Funktion |
|------------------| - | - |
| Textpuffer | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> | Ein Stream der Unicode-Lese-/Schreibzugriff-Text. Es ist möglich, für den Text auf andere Codierungen verwenden. |
| Codefenster | <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> | Ein Dokumentfenster, das eine oder mehrere Textansichten enthält. Wenn [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wird im Modus "Multiple Document Interface (MDI)" wird im Code-Fenster untergeordnetes MDI-Fenster. |
| Textansicht | <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> | Ein Fenster, in dem der Benutzer navigieren, und zeigen Text mithilfe der Tastatur und Maus. Eine Textansicht, die als Editor für den Benutzer angezeigt werden. Sie können der Textansichten in normalen-Editor-Fenster, das Fenster "Ausgabe" und das "Direktfenster" verwenden. Darüber hinaus können Sie eine oder mehrere Textansichten in einem Codefenster konfigurieren. |
| Text-manager | Von verwaltet die <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> -Diensts, über die Sie erhalten eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> Zeiger | Eine Komponente, die allgemeine Informationen, die alle Komponenten, die zuvor beschriebenen freigegebenen verwaltet. |
| Sprachdienst | Hängt von der Implementierung; implementiert <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> | Ein Objekt, das den Editor Sprachspezifische Informationen wie syntaxhervorhebung, Anweisungsvervollständigung und Klammer bietet. |
  
## <a name="see-also"></a>Siehe auch  
 [Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren](../../extensibility/document-data-and-document-view-in-custom-editors.md)
---
title: "Prüfliste: Erstellen eines Vorgängerversion Sprachdiensts | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c06d246f7467e19969075537f321061463d1755
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="checklist-creating-a-legacy-language-service"></a>Prüfliste: Erstellen eines Legacy-Sprachdiensts
Die folgende Checkliste werden zusammengefasst, die grundlegenden Schritte, die Sie ergreifen müssen, damit erstellen Sie einen Sprachdienst für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Core-Editor. Integrieren Sie Ihre Sprache Service in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], müssen Sie eine Debug-ausdrucksauswertung erstellen. Weitere Informationen finden Sie unter [schreiben eine CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) in der [Visual Studio-Debugger-Erweiterbarkeits](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="steps-for-creating-a-language-service"></a>Schritte zum Erstellen eines Sprachdiensts  
  
1.  Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>-Schnittstelle.  
  
    -   In Ihrem VSPackage implementieren die <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Schnittstelle, um der Sprachdienst bereitzustellen.  
  
    -   Der Sprachdienst die integrierte Entwicklungsumgebung (IDE) in zur Verfügung stellen Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Implementierung.  
  
2.  Implementieren der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> -Schnittstelle in die Hauptsprache Dienstklasse.  
  
     Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle ist der Ausgangspunkt der Interaktion zwischen den Core-Editor und der Sprachdienst.  
  
### <a name="optional-features"></a>Optionale Features  
 Die folgenden Funktionen sind optional und können in beliebiger Reihenfolge implementiert werden. Diese Funktionen erhöhen Sie die Funktionalität des Sprachdiensts.  
  
-   Farben für Syntax  
  
     Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>-Schnittstelle. Die Implementierung dieser Schnittstelle sollten die Parser-Informationen, um Informationen über die entsprechende Farbe zurückgegeben.  
  
     Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Methode gibt die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> Schnittstelle. Eine separate Colorizer-Instanz wird für jeden Textpuffer erstellt, damit Sie implementieren sollten die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> separat-Schnittstelle. Weitere Informationen finden Sie unter [Färbung Syntax in ein Legacy-Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
-   Codefenster  
  
     Implementieren der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> -Schnittstelle zum Aktivieren des Sprachdiensts, um benachrichtigt zu werden, wann ein neuer Codefenster erstellt wird.  
  
     Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Methode gibt die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> Schnittstelle. Der Sprachdienst können Sie die spezielle Benutzeroberfläche hinzufügen, um im Codefenster <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>. Der Sprachdienst Gleiches jegliche spezielle Verarbeitung, z. B. das Hinzufügen einer Ansichtsfilter Text in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.  
  
-   Textfilter-Ansicht  
  
     Um IntelliSense-Anweisungsvervollständigung in einen Sprachdienst zu gewährleisten, müssen Sie einige der Befehle abfangen, die andernfalls Textansicht behandelt würden. Um diese Befehle abfangen zu können, müssen führen Sie die folgenden Schritte aus:  
  
    -   Implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> zur Teilnahme an der Command-Kette und Handle-Editor-Befehle.  
  
    -   Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Methode und übergeben Ihr <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Implementierung.  
  
    -   Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> Methode, wenn Sie aus der Ansicht trennen, damit diese Befehle nicht mehr an Sie übergeben werden.  
  
     Befehle, die verarbeitet werden müssen, hängen davon ab, auf die Dienste, die bereitgestellt werden. Weitere Informationen finden Sie unter [wichtige Befehle für Language Service Filter](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
    > [!NOTE]
    >  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> -Schnittstelle muss implementiert werden, auf das gleiche Objekt wie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Schnittstelle.  
  
-   Anweisungsvervollständigung  
  
     Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>-Schnittstelle.  
  
     Unterstützen die Statement-Abschluss-Befehl (also <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>), und rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode in der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> -Schnittstelle, übergeben die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> Schnittstelle. Weitere Informationen finden Sie unter [Anweisungsvervollständigung in einen Legacy-Sprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
-   Methode Tipps  
  
     Implementieren der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> Schnittstelle, um Daten für das QuickInfo-Fenster-Methode bereitzustellen.  
  
     Installieren Sie die Filter für die Text-Ansicht, um Befehle entsprechend zu behandeln, damit Sie wissen, wann eine Methode datentippfenster angezeigt. Weitere Informationen finden Sie unter [ParameterInfo in einen Legacy-Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
-   Fehler-Marker  
  
     Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>-Schnittstelle.  
  
     Erstellen Sie den Fehler Marker-Objekte, implementieren die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> -Schnittstelle, und rufen die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> -Methode auf und übergibt die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> -Schnittstelle des Objekts Marker Fehler.  
  
     Jeder Fehler Marker verwaltet in der Regel ein Element in das Fenster mit Aufgabenliste.  
  
-   Aufgabenlistenelementen  
  
     Implementieren einer Aufgabe Element Klasse Bereitstellen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> Schnittstelle.  
  
     Implementieren einer Aufgabe Anbieter Klasse Bereitstellen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> Schnittstelle und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> Schnittstelle.  
  
     Implementieren einer Aufgabe Enumerator Klasse Bereitstellen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> Schnittstelle.  
  
     Registrieren Sie den Aufgabenanbieter mit der Aufgabenliste <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> Methode.  
  
     Abrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> Schnittstelle durch Aufrufen der Dienstanbieter mit dem Dienst-GUID des Sprachdiensts <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.  
  
     Erstellen Aufgabenobjekten-Element, und rufen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> Methode in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> -Schnittstelle beim vorhanden neu sind oder aktualisiert Aufgaben.  
  
-   Kommentar Aufgabenelementen  
  
     Verwenden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> Schnittstelle und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> Schnittstelle, um den Kommentar Aufgabentoken abzurufen.  
  
     Abrufen einer <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> -Schnittstelle aus dem <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> Dienst.  
  
     Abrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> -Schnittstelle aus dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> Methode.  
  
     Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> Schnittstelle, um die Änderungen in der Tokenliste lauschen.  
  
-   Gliedern  
  
     Es stehen mehrere Optionen für die Unterstützung der Gliederung. Sie können z. B. unterstützen die **Definitionen** Befehl, geben Sie die Editor-gesteuerten Gliederungsbereiche oder unterstützen Regionen Client gesteuert. Weitere Informationen finden Sie unter [Vorgehensweise: Bereitstellen erweitert Gliederung-Unterstützung in einen Legacy-Sprachdienst](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
-   Language Service-Registrierung  
  
     Weitere Informationen dazu, wie Sie einen Sprachdienst zu registrieren, finden Sie unter [registrieren einen Sprachdienst Legacy](../../extensibility/internals/registering-a-legacy-language-service2.md) und [Verwalten von VSPackages](../../extensibility/managing-vspackages.md).  
  
-   Kontextbezogene Hilfe  
  
     Bereitstellen von Kontext auf den Editor in einem der folgenden Methoden:  
  
    -   Bereitstellen von Kontext für Text Marker durch Implementieren der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> Schnittstelle.  
  
 Geben Sie alle Benutzerkontext durch Implementieren der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln von einem Legacy-Sprachdienst](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Schreiben Sie eine CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
---
title: "Pr&#252;fliste: Erstellen einer Legacy-Sprachdienst | Microsoft Docs"
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
  - "Sprachdienste"
  - "Language Services, systemeigenen code"
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Pr&#252;fliste: Erstellen einer Legacy-Sprachdienst
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die folgende Prüfliste werden die grundlegenden Schritte beschrieben, die Reihenfolge einlassen müssen, einen Sprachdienst für den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Kern des Editors zu erstellen.  Um den Sprachdienst in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zu integrieren, müssen Sie einen Debugbuild Ausdrucksauswertung erstellen.  Weitere Informationen finden Sie unter [Schreiben Sie eine CLR\-Ausdrucksauswerter](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) in [Visual Studio\-Debugger\-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## Schritte zum Erstellen eines Sprachdiensts  
  
1.  Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>\-Schnittstelle.  
  
    -   In einem VSPackage implementieren Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>\-Schnittstelle, um den Sprachdienst bereit.  
  
    -   Führen Sie den Sprachdienst für die integrierte Entwicklungsumgebung \(IDE\) in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Implementierung.  
  
2.  Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>\-Schnittstelle in der wichtigsten Sprachdienst Klasse.  
  
     Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>\-Schnittstelle ist der Ausgangspunkt der Interaktion zwischen dem zentralen Editor und dem angegebenen Sprachdienst.  
  
### Optionale Funktionen  
 Die folgenden Funktionen sind optional und können in beliebiger Reihenfolge implementiert werden.  Diese Funktionen erweitern die Funktionalität des Sprachdiensts.  
  
-   Syntaxfarbe  
  
     Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>\-Schnittstelle.  Die Implementierung dieser Schnittstelle, wenn der Parser die entsprechenden Informationen zu Farbinformationen zurückgeben.  
  
     Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>\-Methode gibt die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>\-Schnittstelle zurück.  Eine separate Instanz der farbigen Darstellung wird für jeden Textpuffer erstellt. Daher sollten Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> separat Schnittstelle implementieren.  Weitere Informationen finden Sie unter [Syntaxfarben in eine Legacy\-Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
-   Codefenster  
  
     Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>\-Schnittstelle, um den Sprachdienst den Empfang von Benachrichtigungen, wenn ein neues Codefenster erstellt wird.  
  
     Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>\-Methode gibt die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>\-Schnittstelle zurück.  Der Sprachdienst kann ein spezielles Benutzeroberfläche im Codefenster in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>dann auf Hinzufügen.  Der Sprachdienst kann durch eine spezielle Verarbeitung, beispielsweise das Hinzufügen eines filters der Text im <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>auch tun.  
  
-   Filter der Text  
  
     Um IntelliSense\-Anweisungsvervollständigung in einem Sprachdienst bereitzustellen, müssen Sie einige Befehle abfangen, die die Textansicht Andernfalls behandelt werden würde.  Um diese Befehle abzufangen, führen Sie die folgenden Schritte aus:  
  
    -   Implementieren Sie <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , um eine Verbindung mit der Texteditorbefehle Befehlskette teilzunehmen und zu behandeln.  
  
    -   Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>\-Methode auf, und übergeben Sie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Implementierung.  
  
    -   Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A>\-Methode auf, wenn Sie sich in der Ansicht trennen, sodass diese Befehle nicht mehr Sie übergeben werden.  
  
     Befehle, die behandelt werden müssen, hängt von den Diensten ab, die bereitgestellt werden.  Weitere Informationen finden Sie unter [Wichtige Befehle für Language Service\-Filter](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
    > [!NOTE]
    >  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>\-Schnittstelle muss auf dasselbe Objekt wie die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\-Schnittstelle implementiert werden.  
  
-   Anweisungsvervollständigung  
  
     Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>\-Schnittstelle.  
  
     Sichern Sie den Befehl Anweisungsvervollständigungs \(d. h. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>\) und rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>\-Methode in der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>\-Schnittstelle an, und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>\-Schnittstelle übergeben.  Weitere Informationen finden Sie unter [Abschluss der Anweisung in eine Legacy\-Sprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
-   Methodentipps  
  
     Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>\-Schnittstelle, um Daten für das Fenster tipp Methoden bereitzustellen.  
  
     Installieren Sie den Filter, um Befehle der Text entsprechend zu behandeln, damit Sie wissen, wann ein bezugspunkt\-Tipp Methoden im Fenster anzeigt.  Weitere Informationen finden Sie unter [ParameterInfo in einer Legacy\-Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
-   marker Fehler  
  
     Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>\-Schnittstelle.  
  
     Erstellen Sie die Fehler <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> marker Objekte, die die Schnittstelle implementieren und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>\-Methode aufrufen und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>\-Schnittstelle des Fehlers marker Objekts übergeben.  
  
     In der Regel verwalteten jeder Fehler marker ein Element im Fenster Aufgabenliste.  
  
-   Aufgabenliste Elemente  
  
     Implementieren Sie eine Aufgabenelement Klasse, die die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem>\-Schnittstelle bereitstellt.  
  
     Implementieren Sie eine Klasse, die die Hersteller Aufgaben <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider>\-Schnittstelle und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>\-Schnittstelle bereitstellt.  
  
     Implementieren Sie eine Klasse, die die enumerator Aufgaben <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems>\-Schnittstelle bereitstellt.  
  
     Registrieren Sie den Hersteller der Aufgaben mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A>\-Methode der Aufgabenliste.  
  
     Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>\-Schnittstelle, indem sie den Dienstanbieter GUID des Sprachdiensts mit dem Dienst <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>aufruft.  
  
     Erstellen Sie Aufgabenelement Objekte und rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A>\-Methode in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>\-Schnittstelle an, wenn neue oder aktualisierte Aufgaben vorhanden sind.  
  
-   Kommentartaskelemente  
  
     Verwenden Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>\-Schnittstelle und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>\-Schnittstelle, um die Kommentaraufgaben token.  
  
     Rufen Sie eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>\-Schnittstelle aus dem <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> Dienst.  
  
     Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>\-Schnittstelle aus der <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A>\-Methode.  
  
     Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents>\-Schnittstelle, um auf Änderungen in der Liste Tokens zu überwachen.  
  
-   Gliederung  
  
     Es gibt mehrere Möglichkeiten zum Sichern von Gliederung.  Beispielsweise können Sie den Befehl **Nur Definitionen anzeigen** Unterstützung von einem Editor gesteuert CLIENT\-gesteuerte Bereiche oder Bereiche Kontur Unterstützung zur Verfügung stellen.  Weitere Informationen finden Sie unter [Gewusst wie: unterstützen erweiterte Gliederung in eine Legacy\-Sprachdienst](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
-   Registrierung der Sprachdienst  
  
     Weitere Informationen darüber, wie Sie einen Sprachdienst finden Sie unter [Registrieren einer Legacy\-Sprachdienst](../../extensibility/internals/registering-a-legacy-language-service2.md) und [Verwalten von VSPackages](../../extensibility/managing-vspackages.md)registriert.  
  
-   Kontextbezogene Hilfe  
  
     Bereitstellen von Kontext in den Editor mit einer der folgenden Methoden zur Verfügung:  
  
    -   Bereitstellen von Kontext für Textmarkierungen aus dem Implementieren der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>\-Schnittstelle bereit.  
  
 Stellen Sie alle Benutzerkontext aus dem Implementieren der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>\-Schnittstelle bereit.  
  
## Siehe auch  
 [Entwickeln einer Sprache](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Schreiben Sie eine CLR\-Ausdrucksauswerter](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
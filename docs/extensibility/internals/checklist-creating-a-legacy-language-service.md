---
title: 'Checkliste: Erstellen eines Legacy-Sprachdienstes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11785dab63cbb6a95ab2d34c5edbfb4525ebf34c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709789"
---
# <a name="checklist-create-a-legacy-language-service"></a>Checkliste: Erstellen eines älteren Sprachdienstes
Die folgende Checkliste fasst die grundlegenden Schritte zusammen, die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Sie ausführen müssen, um einen Sprachdienst für den Kerneditor zu erstellen. Um Ihren Sprachdienst [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]in zu integrieren, müssen Sie einen Debugausdruck-Evaluator erstellen. Weitere Informationen finden Sie unter [Schreiben eines CLR-Ausdrucksevaluators](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) in visual [Studio-Debuggererweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="steps-to-create-a-language-service"></a>Schritte zum Erstellen eines Sprachdienstes

1. Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>-Schnittstelle.

    - Implementieren Sie in Ihrem <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> VSPackage die Schnittstelle, um den Sprachdienst bereitzustellen.

    - Stellen Sie Ihren Sprachdienst der integrierten Entwicklungsumgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> (IDE) in Ihrer Implementierung zur Verfügung.

2. Implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Sie die Schnittstelle in der Hauptsprachdienstklasse.

     Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Schnittstelle ist der Ausgangspunkt der Interaktion zwischen dem Kerneditor und dem Sprachdienst.

### <a name="optional-features"></a>Optionale Features
 Die folgenden Funktionen sind optional und können in beliebiger Reihenfolge implementiert werden. Diese Funktionen erhöhen die Funktionalität Ihres Sprachdienstes.

- Farben für Syntax

  Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>-Schnittstelle. Ihre Implementierung dieser Schnittstelle sollte die Parser-Informationen die entsprechenden Farbinformationen zurückgeben.

  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Methode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> gibt die Schnittstelle zurück. Für jeden Textpuffer wird eine separate Colorizer-Instanz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> erstellt, daher sollten Sie die Schnittstelle separat implementieren. Weitere Informationen finden Sie unter [Syntaxfarben in einem älteren Sprachdienst](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).

- Codefenster

  Implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> Sie die Schnittstelle, damit der Sprachdienst benachrichtigungsfähig ist, wenn ein neues Codefenster erstellt wird.

  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Methode <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> gibt die Schnittstelle zurück. Der Sprachdienst kann dann dem Codefenster <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>in eine spezielle Benutzeroberfläche hinzufügen. Der Sprachdienst kann auch eine spezielle Verarbeitung durchgehen, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>z. B. das Hinzufügen eines Textansichtsfilters in .

- Textansichtsfilter

  Um die Vervollständigung der IntelliSense-Anweisung in einem Sprachdienst bereitzustellen, müssen Sie einige der Befehle abfangen, die die Textansicht andernfalls verarbeiten würde. Führen Sie die folgenden Schritte aus, um diese Befehle abzufangen:

  - Implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Sie, um an der Befehlskette teilzunehmen und Editorbefehle zu behandeln.

  - Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> Sie die Methode <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> auf, und übergeben Sie die Implementierung.

  - Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> Sie die Methode auf, wenn Sie sich von der Ansicht trennen, damit diese Befehle nicht mehr an Sie übergeben werden.

  Befehle, die behandelt werden müssen, hängen von den bereitgestellten Diensten ab. Weitere Informationen finden Sie unter [Wichtige Befehle für Sprachdienstfilter](../../extensibility/internals/important-commands-for-language-service-filters.md).

  > [!NOTE]
  > Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Schnittstelle muss auf demselben Objekt <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> wie die Schnittstelle implementiert werden.

- Anweisungsvervollständigung

  Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>-Schnittstelle.

  Unterstützen Sie den Befehl "Anweisungsvervollständigung" <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>(d. h.) und rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode in der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Schnittstelle auf, indem Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> Schnittstelle übergeben. Weitere Informationen finden Sie unter [Abschluss der Anweisung in einem älteren Sprachdienst](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

- Methodentipps

  Implementieren <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> Sie die Schnittstelle, um Daten für das Methodentippfenster bereitzustellen.

  Installieren Sie den Textansichtsfilter, um Befehle entsprechend zu behandeln, damit Sie wissen, wann ein Methodendatentippfenster angezeigt werden soll. Weitere Informationen finden Sie unter [Parameterinformationen in einem älteren Sprachdienst](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).

- Fehlermarkierungen

  Implementieren Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>-Schnittstelle.

  Erstellen Sie die Fehlermarkerobjekte, die die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle implementieren und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> Methode aufrufen, indem Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> Schnittstelle des Fehlermarkerobjekts übergeben.

  In der Regel verwaltet jede Fehlermarkierung ein Element im Aufgabenlistenfenster.

- Aufgabenlistenelemente

  Implementieren Sie eine Aufgabenelementklasse, die die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> Schnittstelle bereitstellt.

  Implementieren Sie eine Aufgabenanbieterklasse, die die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> Schnittstelle und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> Schnittstelle bereitstellt.

  Implementieren Sie eine Taskenumeratorklasse, die die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> Schnittstelle bereitstellt.

  Registrieren Sie den Aufgabenanbieter mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> der Methode der Aufgabenliste.

  Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> Sie die Schnittstelle ab, indem Sie den <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>Dienstanbieter des Sprachdienstes mit der Dienst-GUID aufrufen.

  Erstellen Sie Aufgabenelementobjekte, und rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> Methode in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> Schnittstelle auf, wenn neue oder aktualisierte Aufgaben vorhanden sind.

- Kommentaraufgabenelemente

  Verwenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> Schnittstelle und die Schnittstelle, um die Kommentaraufgabentoken abzurufen.

  Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> Sie eine <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> Schnittstelle vom Dienst ab.

  Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> Schnittstelle von der Methode ab.

  Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> Sie die Schnittstelle, um auf Änderungen in der Tokenliste zu achten.

- Gliedern

  Es gibt mehrere Möglichkeiten, um die Gliederung zu unterstützen. Sie können z. B. den Befehl **"Auf Definitionen reduzieren"** unterstützen, gleisten gesteuerte Gliederungsbereiche bereitstellen oder clientgesteuerte Regionen unterstützen. Weitere Informationen finden Sie unter [Gewusst wie: Bereitstellen erweiterter Gliederungsunterstützung in einem älteren Sprachdienst](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).

- Sprachdienstregistrierung

  Weitere Informationen zum Registrieren eines Sprachdienstes finden Sie unter [Registrieren eines älteren Sprachdienstes](../../extensibility/internals/registering-a-legacy-language-service2.md) und [Verwalten von VSPackages](../../extensibility/managing-vspackages.md).

- Kontextsensitive Hilfe

  Stellen Sie dem Editor auf eine der folgenden Arten Kontext bereit:

  - Stellen Sie Kontext für Textmarkierungen bereit, indem Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> Schnittstelle implementieren.

  - Stellen Sie den gesamten <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> Benutzerkontext bereit, indem Sie die Schnittstelle implementieren.

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln eines älteren Sprachdienstes](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Schreiben eines CLR-Ausdrucksevaluators](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

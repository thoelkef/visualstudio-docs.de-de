---
title: Legacy-Sprachdienst Schnittstellen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IVsLanguageInfo interface
- language services, objects
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 065ef972709ca78b516a9acc5f4a737d2963e4b7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726848"
---
# <a name="legacy-language-service-interfaces"></a>Schnittstellen von Legacysprachdiensten
Für eine bestimmte Programmiersprache kann jeweils nur eine Instanz eines sprach Dienstanbieter vorhanden sein. Ein einzelner Sprachdienst kann jedoch mehr als einen Editor verarbeiten.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verknüpft einen Sprachdienst keinem bestimmten Editor. Wenn Sie also einen Sprachdienst Vorgang anfordern, müssen Sie den entsprechenden Editor als Parameter angeben.

## <a name="common-interfaces-associated-with-language-services"></a>Allgemeine Schnittstellen, die Sprachdiensten zugeordnet sind
 Der Editor Ruft den Sprachdienst ab, indem <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> im entsprechenden VSPackage aufgerufen wird. Die in diesem-Befehl ausgeführte Dienst-ID (SID) identifiziert den angeforderten Sprachdienst.

 Sie können die Schnittstellen des Kern sprach Dienstanbieter für eine beliebige Anzahl von separaten Klassen implementieren. Eine gängige Vorgehensweise besteht jedoch darin, die folgenden Schnittstellen in einer einzigen Klasse zu implementieren:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> (optional)

  Die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>-Schnittstelle muss für alle Sprachdienste implementiert werden. Sie enthält Informationen zu Ihrem Sprachdienst, wie z. b. den lokalisierten Namen der Sprache, die Dateinamen Erweiterungen, die dem Sprachdienst zugeordnet sind, und das Abrufen einer Farbgebung.

## <a name="additional-language-service-interfaces"></a>Zusätzliche Sprachdienst Schnittstellen
 Andere Schnittstellen können mit Ihrem Sprachdienst bereitgestellt werden. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fordert eine separate Instanz dieser Schnittstellen für jede Instanz des Text Puffers an. Daher sollten Sie jede dieser Schnittstellen in einem eigenen-Objekt implementieren. In der folgenden Tabelle sind Schnittstellen aufgeführt, für die eine Instanz pro Text Puffer Instanz erforderlich ist.

|Interface|Beschreibung|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Verwaltet Code Fenster-Zusatzelemente, wie z. b. die Dropdown Leiste. Sie können diese Schnittstelle mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>-Methode erhalten. Pro Code Fenster gibt es eine <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Farmiert sprach Schlüsselwörter und Trennzeichen. Sie können diese Schnittstelle mit der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>-Methode erhalten. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> wird zur zeichnungszeit aufgerufen. Vermeiden Sie eine rechenintensive Arbeit innerhalb <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>, oder die Leistung kann beeinträchtigt werden.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Stellt Quick Infos für IntelliSense-Parameter bereit. Wenn der Sprachdienst ein Zeichen erkennt, das angibt, dass Methoden Daten angezeigt werden sollen, z. b. eine öffnende Klammer, ruft es die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>-Methode auf, um die Textansicht zu benachrichtigen, dass der Sprachdienst zum Anzeigen einer QuickInfo für die Parameter Info bereit ist. Die Textansicht ruft dann wieder den Sprachdienst auf, indem Sie die Methoden der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>-Schnittstelle verwendet, um die erforderlichen Informationen zum Anzeigen der QuickInfo zu erhalten.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Bietet die IntelliSense-Anweisungs Vervollständigung. Wenn der Sprachdienst bereit ist, eine Vervollständigungsliste anzuzeigen, ruft er die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>-Methode für die Textansicht auf. Die Textansicht ruft dann den Sprachdienst mithilfe von Methoden für das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> Objekt zurück.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Ermöglicht das Ändern der Textansicht mithilfe des Befehls Handlers. Die Klasse, in der Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>-Schnittstelle implementieren, muss auch die <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>-Schnittstelle implementieren. Die Textansicht Ruft das <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Objekt ab, indem das <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Objekt abgefragt wird, das an die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>-Methode weitergegeben wird. Für jede Ansicht sollte ein <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Objekt vorhanden sein.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Fängt die Befehle ab, die vom Benutzer in das Code Fenster eingetippt werden. Überwachen der Ausgabe ihrer <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>-Implementierung, um benutzerdefinierte Vervollständigungs Informationen bereitzustellen und Änderungen anzuzeigen<br /><br /> Um das <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Objekt an die Textansicht zu übergeben, wenden Sie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> an.|

## <a name="see-also"></a>Siehe auch
- [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Prüfliste: Erstellen eines Legacysprachdiensts](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)
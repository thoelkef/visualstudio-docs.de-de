---
title: Wichtige Befehle für Sprachdienst Filter | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0e2e605a0725c2f88922d3e3ce899263171bc4d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726926"
---
# <a name="important-commands-for-language-service-filters"></a>Wichtige Befehle für Sprachdienstfilter
Wenn Sie einen voll funktionsfähigen Sprachdienst Filter erstellen möchten, sollten Sie die folgenden Befehle verarbeiten. Die vollständige Liste der Befehls Bezeichner wird in der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>-Enumeration für verwalteten Code und in der Header Datei stdidcmd. h für nicht verwalteten [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Code definiert. Sie finden die Datei "stdidcmd. h" im *Visual Studio SDK-Installationspfad*\visualstudiointegration\common\inc.

## <a name="commands-to-handle"></a>Zu behandelnde Befehle

> [!NOTE]
> Es ist nicht erforderlich, für jeden Befehl in der folgenden Tabelle zu filtern.

|Befehl|Beschreibung|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird gesendet, wenn der Benutzer mit der rechten Maustaste klickt. Dieser Befehl gibt an, dass es an der Zeit ist, ein Kontextmenü anzugeben. Wenn Sie diesen Befehl nicht verarbeiten, stellt der Text-Editor ein Standardkontext Menü ohne sprachspezifische Befehle bereit. Wenn Sie Ihre eigenen Befehle in dieses Menü einschließen möchten, behandeln Sie den Befehl, und zeigen Sie selbst ein Kontextmenü an.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird normalerweise gesendet, wenn der Benutzer STRG + J eingibt. Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>-Methode auf dem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> auf, um das Feld Anweisungs Vervollständigung anzuzeigen.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird gesendet, wenn der Benutzer ein Zeichen eingibt. Überwachen Sie diesen Befehl, um zu bestimmen, wann ein auslöserzeichen eingegeben wurde und wie Sie Anweisungs Vervollständigung, Methoden Tipps und Textmarker bereitstellen, z. b. Syntax Farben, übereinstimmende Klammern und Fehler Marker. Ruft die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>-Methode für den <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> für die Anweisungs Vervollständigung und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>-Methode auf dem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> für Methoden Tipps auf. Zur Unterstützung von Text Markern überwachen Sie diesen Befehl, um zu bestimmen, ob das typisierte Zeichen die Aktualisierung der Marker erfordert.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird gesendet, wenn der Benutzer die EINGABETASTE eingibt. Überwachen Sie diesen Befehl, um zu bestimmen, wann ein Methoden Tipp Fenster durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>-Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> geschlossen werden soll. Standardmäßig wird dieser Befehl in der Textansicht behandelt.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird gesendet, wenn der Benutzer die RÜCKTASTE eingibt. Monitor, um zu bestimmen, wann ein Methoden Tipp Fenster durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>-Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> geschlossen werden soll. Standardmäßig wird dieser Befehl in der Textansicht behandelt.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet von einem Menü oder einer Tastenkombination. Aufrufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>-Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, um das Tip-Fenster mit den Parameterinformationen zu aktualisieren.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird gesendet, wenn der Benutzer auf eine Variable zeigt oder den Cursor auf einer Variablen positioniert und im Menü **Bearbeiten** **Quick Infos** aus **IntelliSense** auswählt. Gibt den Typ der Variablen in einem Trinkgeld zurück, indem die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>-Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> aufgerufen wird. Wenn das Debuggen aktiv ist, sollte der Tipp auch den Wert der Variablen anzeigen.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird normalerweise gesendet, wenn der Benutzer STRG + LEERTASTE eingibt. Dieser Befehl weist den Sprachdienst an, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>-Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> aufzurufen.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird von einem Menü gesendet, in der **Regel im Menü** " **Bearbeiten** ", um die Auswahl zu **kommentieren** oder die **Auskommentierung der Auswahl** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> gibt an, dass der Benutzer den markierten Text auskommentieren möchte.  <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> gibt an, dass der Benutzer die Auskommentierung des ausgewählten Texts aufheben möchte. Diese Befehle können nur vom Sprachdienst implementiert werden.|

## <a name="see-also"></a>Siehe auch
- [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)
---
title: Wichtige Befehle für Sprachdienstfilter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb29ee5b5a5359d6cfe34911656dfe9be015262e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707617"
---
# <a name="important-commands-for-language-service-filters"></a>Wichtige Befehle für Sprachdienstfilter
Wenn Sie einen voll funktionsfähigen Sprachdienstfilter erstellen möchten, sollten Sie die folgenden Befehle verwenden. Die vollständige Liste der Befehlsbezeichner ist in der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Enumeration für verwalteten Code [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] und in der Stdidcmd.h-Headerdatei für nicht verwalteten Code definiert. Sie finden die Datei Stdidcmd.h im *Installationspfad von Visual Studio SDK.*

## <a name="commands-to-handle"></a>Zu behandelnde Befehle

> [!NOTE]
> Es ist nicht obligatorisch, nach jedem Befehl in der folgenden Tabelle zu filtern.

|Get-Help|BESCHREIBUNG|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird gesendet, wenn der Benutzer mit der rechten Maustaste klickt. Dieser Befehl gibt an, dass es an der Zeit ist, ein Kontextmenü bereitzustellen. Wenn Sie diesen Befehl nicht verwenden, stellt der Texteditor ein Standard-Kontextmenü ohne sprachspezifische Befehle bereit. Um Ihre eigenen Befehle in dieses Menü einzuschließen, behandeln Sie den Befehl und zeigen Sie selbst ein Kontextmenü an.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird in der Regel gesendet, wenn der Benutzer STRG+J eingibt. Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Methode auf der auf, um das Anweisungsvervollständigungsfeld anzuzeigen.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird gesendet, wenn der Benutzer ein Zeichen eingibt. Überwachen Sie diesen Befehl, um zu bestimmen, wann ein Triggerzeichen eingegeben wird, und um Anweisungsvervollständigung, Methodentipps und Textmarkierungen wie Syntaxfarben, Klammerabgleich und Fehlermarkierungen bereitzustellen. Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Methode für <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> die for-Anweisungsvervollständigung und die Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> for-Methodentipps auf. Um Textmarkierungen zu unterstützen, überwachen Sie diesen Befehl, um zu bestimmen, ob das eingegebene Zeichen erfordert, dass Sie die Marker aktualisieren.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird gesendet, wenn der Benutzer den Enter-Schlüssel eingibt. Überwachen Sie diesen Befehl, um zu bestimmen, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> wann <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>ein Methodentippfenster durch Aufrufen der Methode auf der verworfen werden soll. Standardmäßig behandelt die Textansicht diesen Befehl.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird gesendet, wenn der Benutzer den Backspace-Schlüssel eingibt. Überwachen Sie, wann ein Methodentippfenster <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> durch Aufrufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>der Methode auf der verworfen werden soll. Standardmäßig behandelt die Textansicht diesen Befehl.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird über ein Menü oder eine Tastenkombination gesendet. Rufen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Methode auf der auf, um das Tip-Fenster mit den Parameterinformationen zu aktualisieren.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird gesendet, wenn der Benutzer den Mauszeiger über eine Variable zeigt oder den Cursor auf einer Variablen positioniert und im Menü **Bearbeiten** **Quick Info** aus **IntelliSense** auswählt. Geben Sie den Typ der Variablen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> in einer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>Spitze zurück, indem Sie die Methode auf der aufrufen. Wenn das Debuggen aktiv ist, sollte der Tipp auch den Wert der Variablen anzeigen.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird in der Regel gesendet, wenn der Benutzer STRG+SPACEBAR eingibt. Dieser Befehl weist den Sprachdienst an, die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode auf der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>aufzurufen.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Wird aus einem Menü gesendet, in der Regel **Kommentarauswahl** oder **Nichtkommentarauswahl** aus **"Erweitert"** im Menü **Bearbeiten.** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>gibt an, dass der Benutzer den ausgewählten Text auskommentieren möchte. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> gibt an, dass der Benutzer die Kommentierung des ausgewählten Textes aufdecken möchte. Diese Befehle können nur vom Sprachdienst implementiert werden.|

## <a name="see-also"></a>Weitere Informationen
- [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)

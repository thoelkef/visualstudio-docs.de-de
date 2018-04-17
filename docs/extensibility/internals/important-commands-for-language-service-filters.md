---
title: Wichtige Befehle für Language Service Filter | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1e7affdbcad2b935a05420a2817c5d8bda5cd9cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="important-commands-for-language-service-filters"></a>Wichtig-Befehle für Language Service-Filter
Wenn Sie einen voll funktionsfähiges Sprachfilter für den Dienst erstellen möchten, erwägen Sie, behandeln die folgenden Befehle. Die vollständige Liste der Befehls-IDs wird definiert, der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> bei nicht verwalteten Enumeration für verwalteten Code und den Stdidcmd.h-Header-Datei [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Code. Sie finden die Datei Stdidcmd.h in *Visual Studio SDK-Installationspfad*\VisualStudioIntegration\Common\Inc.  
  
## <a name="commands-to-handle"></a>Befehle zum Handle  
  
> [!NOTE]
>  Es ist nicht erforderlich, um für jeden Befehl in der folgenden Tabelle filtern.  
  
|Befehl|Beschreibung|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet, wenn der Benutzer klickt. Dieser Befehl gibt an, dass ein Kontextmenü bereitgestellt werden. Wenn Sie diesen Befehl nicht behandelt, stellt der Text-Editor ein Standard-Kontextmenü ohne sprachspezifische Befehle bereit. Um eine eigene Befehle in diesem Menü sind verfügbar, den Befehl behandelt, und selbst ein Kontextmenü anzeigen.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|In der Regel gesendet, wenn der Benutzer STRG + J eingibt. Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> anzuzeigende Feld Abschluss-Anweisung.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet, wenn der Benutzer ein Zeichen eingibt. Überwachen Sie diesen Befehl, um zu ermitteln, wann ein triggerzeichen eingegeben typisiert ist, und um-Anweisung für Abschluss, Methode Tipps und Text-Marker, z. B. Syntaxfarben Klammer und Fehler Marker. Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> für die Anweisungsvervollständigung und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> Methode auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> Methode Tipps. Überwachen Sie, um Text Marker unterstützen, diesen Befehl aus, um zu bestimmen, ob das Zeichen eingegeben wird, müssen Sie die Marker aktualisieren.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet, wenn der Benutzer die EINGABETASTE eingibt. Überwachen Sie diesen Befehl, um zu bestimmen, wann Sie durch Aufrufen einer Methode QuickInfo-Fenster zu schließen die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Standardmäßig behandelt der Textansicht mit diesem Befehl.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet, wenn der Benutzer die RÜCKTASTE eingibt. Monitor zum Ermitteln, wann eine Methode QuickInfo-Fenster zu schließen, durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Standardmäßig behandelt der Textansicht mit diesem Befehl.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Aus einem Menü oder einer Tastenkombination gesendet. Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> Methode auf die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> auf das QuickInfo-Fenster mit den Parameter zu aktualisieren.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet, wenn der Benutzer über eine Variable bewegt wird, oder den Cursor auf eine Variable positioniert und wählt **Quick Info** aus **IntelliSense** in der **bearbeiten** Menü. Den Typ der Variablen in einer QuickInfo zurückkehren, indem die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Wenn Debuggen aktiviert ist, sollte der Tipp auch den Wert der Variablen anzeigen.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|In der Regel gesendet, wenn der Benutzer STRG + LEERTASTE eingibt. Dieser Befehl weist der Sprachdienst zum Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|In der Regel aus einem Menü gesendet **Kommentarauswahl** oder **Auswahl kommentieren** aus **erweitert** in der **bearbeiten** Menü. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Gibt an, dass der Benutzer möchte den markierten Text auskommentieren. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> gibt an, dass der Benutzer möchte, um den markierten Text auszukommentieren. Diese Befehle können nur von der Sprachdienst implementiert werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)
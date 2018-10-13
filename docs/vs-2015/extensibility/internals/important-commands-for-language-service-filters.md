---
title: Wichtige Befehle für Language Service-Filter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f2cceeffe22422abb9648d75e669cf74ff0b17e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49175278"
---
# <a name="important-commands-for-language-service-filters"></a>Wichtige Befehle für Sprachdienstfilter
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn Sie einen voll funktionsfähiges Service Sprachfilter erstellen möchten, sollten Sie behandeln die folgenden Befehle aus. Die vollständige Liste der Befehls-IDs wird definiert, der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Enumeration für verwalteten Code und den Stdidcmd.h-Header-Datei für nicht verwaltete [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] Code. Sie finden die Datei Stdidcmd.h in *Visual Studio SDK-Installationspfad*\VisualStudioIntegration\Common\Inc.  
  
## <a name="commands-to-handle"></a>Befehle zum Handle  
  
> [!NOTE]
>  Es ist nicht erforderlich, um für jeden Befehl in der folgenden Tabelle filtern.  
  
|Befehl|Beschreibung|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet, wenn der Benutzer klickt. Dieser Befehl gibt an, dass es Zeit, um ein Kontextmenü bereitzustellen ist. Wenn Sie diesen Befehl nicht behandeln, stellt der Text-Editor ein standardmäßigen Kontextmenü ohne sprachspezifische Befehle bereit. Um Ihre eigenen Befehle in diesem Menü einzuschließen, behandeln Sie den Befehl aus, und zeigen Sie selbst ein Kontextmenü an.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|In der Regel gesendet, wenn der Benutzer STRG + J eingibt. Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> abschlussfeld Anweisung angezeigt.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet, wenn der Benutzer ein Zeichen eingibt. Überwachen Sie diesen Befehl, um zu ermitteln, wann ein triggerzeichen eingegeben typisiert ist und zum Bereitstellen der Anweisung Abschluss methodentipps und Textmarkierungen, z. B. farbliche syntaxkennzeichnung, Klammer und fehlermarker. Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> für die Anweisungsvervollständigung und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> Methode Tipps. Zur Unterstützung von Textmarkierungen überwachen Sie diesen Befehl, um zu bestimmen, ob das Zeichen eingegeben wird, müssen Sie Ihre Markierungen aktualisieren.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet, wenn der Benutzer die EINGABETASTE eingibt. Überwachen Sie diesen Befehl, um zu bestimmen, wann ein methodentippfenster zu schließen, durch den Aufruf der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Standardmäßig behandelt die Textansicht mit diesem Befehl.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet, wenn der Benutzer mit die RÜCKTASTE eingibt. Monitor, um zu bestimmen, wann ein methodentippfenster zu schließen, durch den Aufruf der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. Standardmäßig behandelt die Textansicht mit diesem Befehl.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet von einem Menü oder eine Tastenkombination. Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> der QuickInfo-Fenster mit den Parameterinformationen zu aktualisieren.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet, wenn der Benutzer auf eine Variable zeigen oder den Cursor in eine Variable positioniert und wählt **Quick Info** aus **IntelliSense** in die **bearbeiten** Menü. Den Typ der Variablen in einem Tipp zurückkehren, indem die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Wenn Debuggen aktiv ist, sollte den Wert der Variablen auch die QuickInfo angezeigt werden.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|In der Regel gesendet, wenn der Benutzer STRG + LEERTASTE eingibt. Dieser Befehl weist den Sprachdienst, zum Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Methode für die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet von einem Menü, in der Regel **Auswahl kommentieren** oder **Kommentar der Auswahl** aus **erweitert** in die **bearbeiten** Menü. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Gibt an, dass der Benutzer den ausgewählten Text kommentieren möchte; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> gibt an, dass der Benutzer den markierten Text kommentieren möchte. Diese Befehle können nur vom Sprachdienst implementiert werden.|  
  
## <a name="see-also"></a>Siehe auch  
 [Entwickeln eines Legacysprachdiensts](../../extensibility/internals/developing-a-legacy-language-service.md)


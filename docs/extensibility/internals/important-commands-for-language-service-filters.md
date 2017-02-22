---
title: "Wichtige Befehle f&#252;r Language Service-Filter | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Language Services, Filter"
  - "Language Services, Befehle unterstützen"
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# Wichtige Befehle f&#252;r Language Service-Filter
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn Sie einen voll gekennzeichneten Sprachdienst Filter erstellen möchten, sollten Sie die folgenden Befehle zu behandeln.  Die vollständige Liste der Befehlsbezeichner wird in der <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>\-Enumeration für verwalteten Code und in der Stdidcmd.h\-Headerdatei für nicht verwalteten Code [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] definiert.  Sie können die Stdidcmd.h\-Datei in *Pfad SDK\-Installations Visual Studio*\\ VisualStudioIntegration \\ Common \\ Inc. suchen.  
  
## Behandeln von Befehlen  
  
> [!NOTE]
>  So filtern ist nicht erforderlich, um für jeden Befehl in der folgenden Tabelle.  
  
|Befehl|Beschreibung|  
|------------|------------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet, wenn der Benutzer mit der rechten Maustaste klickt.  Dieser Befehl gibt an, dass der Uhrzeit ist, wird ein Kontextmenü bereitzustellen.  Wenn Sie diesen Befehl behandeln, wird im Editor ein standardmäßiges Kontextmenü ohne sprachspezifische Befehlen bereit.  Um in diesem Menü auf Befehle enthalten sind, behandeln Sie den Befehl und zeigen Sie ein Kontextmenü auf.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Normalerweise gesendet, wenn der Benutzer STRG\+J.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>\-Methode auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> auf, um das Feld Anweisungsvervollständigungs anzuzeigen.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet wenn der Benutzer ein Zeichen.  Überwachen Sie diesen Befehl, um zu bestimmen, wann ein Trigger Zeichen eingegeben wird und die Anweisungsvervollständigung, Methoden und tipps Textmarkierungen, wie Syntaxfarbe bereitstellen, abstützen Vergleiche und Fehler marker.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>\-Methode auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> für die Anweisungsvervollständigung und die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>\-Methode auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> für Methoden tipps an.  Zur Unterstützung von Textmarkierungen überwachen Sie diesen Befehl zu bestimmen, ob das Zeichen eingegeben werden muss die Markierung aktualisieren.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet wenn der Benutzer die EINGABETASTE.  Überwachen Sie diesen Befehl, um zu bestimmen, wann ein tipp Methoden im Fenster entlässt, indem Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>\-Methode auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>aufrufen.  Standardmäßig behandelt die Textansicht diesen Befehl.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet wenn der Benutzer die RÜCKTASTE.  Bildschirm zu bestimmen, wann ein tipp Methoden im Fenster durch Aufrufen der <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>\-Methode auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>entlässt.  Standardmäßig behandelt die Textansicht diesen Befehl.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet in einem Menü oder einer Zugriffstaste.  Rufen Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>\-Methode auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> an, um das Fenster mit den Tipp Parameterinformationen zu aktualisieren.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet, wenn der Benutzer auf eine Variable oder Positioniert den Cursor in einer Variablen zeigt, und **QuickInfo** von **IntelliSense** im Menü **Bearbeiten** auswählt.  Geben Sie den Typ der Variablen in einem Spitze zurück, indem Sie die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>\-Methode auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>aufrufen.  Wenn das Debuggen aktiviert ist, sollte der Spitze der Wert der Variablen auch anzeigen.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Normalerweise gesendet, wenn der Benutzer STRG\+LEERTASTE.  Dieser Befehl wird der Sprachdienst, um die <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>\-Methode auf <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>aufzurufen.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Gesendet aus einem Menü, in der Regel von **Auswahl kommentieren** oder **Auskommentierung der Auswahl aufheben** von **Erweitert** im Menü **Bearbeiten** .  <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> gibt an, dass der Benutzer möchte Kommentieren Sie den markierten Text. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> gibt an, dass der Benutzer auf den markierten Text aufgehoben werden soll.  Diese Befehle können nur vom Sprachdienst implementiert werden.|  
  
## Siehe auch  
 [Entwickeln einer Sprache](../../extensibility/internals/developing-a-legacy-language-service.md)
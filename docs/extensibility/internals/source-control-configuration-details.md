---
title: "Source Control-Konfigurationsdetails | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Datenquellen-Steuerelement [Visual Studio SDK] Konfigurationsdetails"
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Source Control-Konfigurationsdetails
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Um die Quellcodeverwaltung zu implementieren, müssen Sie das Projektsystem ordnungsgemäß konfigurieren oder den Editor für folgende Aufgaben:  
  
-   Auffordern Berechtigung geändertem Zustands, in den gewechselt werden soll  
  
-   Anfordern einer Berechtigung zum Speichern von Dateien  
  
-   Fordern Sie Dateien des Projekts die Berechtigung zum Hinzufügen, Entfernen oder Umbenennen  
  
## Anforderungs\-Berechtigung geändertem Zustands, in den gewechselt werden soll  
 Ein Projekt oder ein Editor müssen über die Berechtigung für den Übergang in den modifizierten \(\) geänderten Zustand anfordern, indem <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>aufrufen.  Jeder Editor, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> implementiert, muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> aufrufen und Genehmigung empfangen, um das Dokument von der Umgebung zu ändern, bevor er `True` für `M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`zurückgibt.  Ein Projekt ist im Wesentlichen ein Editor für eine Projektdatei, und infolgedessen, hat die gleiche Aufgabe zum Implementieren von dem geänderten Zustand, der für die Projektdatei nachverfolgt, z. B. einen Text\-Editor für die zugehörigen Dateien ausführt.  Die Umgebung behandelt den geänderten Zustand der Projektmappe, aber Sie müssen den geänderten Zustand eines beliebigen Objekts behandeln die Projektmappe Verweise nicht speichern, sondern z. B. eine Projektdatei oder ihre Elemente.  Im Allgemeinen wenn das Projekt oder der Editor zum Verwalten der Persistenz für ein Element zuständig ist, dann ist für die Implementierung Geänderte Zustand Nachverfolgung verantwortlich.  
  
 Als Reaktion auf den `IVsQueryEditQuerySave2::QueryEditFiles` Aufruf kann die Umgebung wie folgt vorgehen:  
  
-   Weisen Sie den Aufruf zurückgegeben, um zu ändern. In diesem Fall wird der Editor oder das Projekt im unveränderten \(bereinigten Zustand\) bleiben müssen.  
  
-   Geben Sie an, dass die Dokumentdaten erneut geladen werden sollen.  Bei einem Projekt erneut lädt die Umgebung die Daten für das Projekt.  Ein Editor muss die Daten durch seine Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Datenträger aktualisieren.  In jedem Fall kann der Kontext im Projekt oder der Editor ändern, wenn die Daten erneut geladen wird.  
  
 Es handelt sich um eine komplexe und schwierige Aufgabe, den entsprechenden `IVsQueryEditQuerySave2::QueryEditFiles` Aufrufe einer vorhandenen CodeBase nachzurüsten.  Daher sollten diese Aufrufe während der Erstellung des Projekts oder des Editors integriert werden.  
  
## Anforderungs\-Berechtigung Speichern einer Datei  
 Vor einem Projekt oder einem Editor speichert eine Datei, muss sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>aufrufen.  Für Projektdateien werden diese Aufrufe automatisch durch die Projektmappe abgeschlossen, die weiß, wann eine Projektdatei speichert.  Editoren sind für diese Aufrufe zuständig, es sei denn, die von `IVsPersistDocData2` Implementierung der Editor das Hilfsfunktions <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>verwendet.  Wenn der Editor `IVsPersistDocData2` auf diese Weise implementiert, wird der Aufruf `IVsQueryEditQuerySave2::QuerySaveFile` oder `IVsQueryEditQuerySave2::QuerySaveFiles` für Sie erstellt.  
  
> [!NOTE]
>  Führen Sie immer diese Aufrufe Vorkaufs\-dass ist, zu einer bestimmten Uhrzeit als Editor in der Lage ist, einen Löschvorgang zu empfangen.  
  
## Fordern Sie Dateien des Projekts die Berechtigung zum Hinzufügen, Entfernen oder Umbenennen  
 Bevor ein Projekt eine Datei oder ein Verzeichnis hinzufügen, umbenennen oder entfernen kann, muss er die entsprechende `IVsTrackProjectDocuments2::OnQuery*`\-Methode aufrufen, um die Berechtigung aus der Umgebung anfordern.  Wenn die Berechtigung erteilt wird, muss das Projekt den Vorgang abschließen und die entsprechende `IVsTrackProjectDocuments2::OnAfter*`\-Methode aufrufen, um sie zu benachrichtigen, wenn der Vorgang abgeschlossen ist.  Das Projekt muss die Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>\-Schnittstelle für alle Dateien \(z. B. Gerätedateien\) und nicht nur die Elemente Dateien aufrufen.  Aufrufe von Dateien erforderlich sind, aber Verzeichnis Aufrufe sind optional.  Wenn es sich bei dem Projekt um Verzeichnisinformationen verfügt, sollte er die entsprechenden Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> , aber wenn es keine Informationen enthält, die Umgebung durch einen Aufruf von Verzeichnisinformationen.  
  
 Das Projekt sollte die Methoden von `IVsTrackProjectDocuments2` Öffnen oder Schließen nicht am Projekt aufzurufen.  Listener, die beim Start dieser Informationen können <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> auf das Ereignis warten und von der Lösung durchlaufen, um die Daten zu finden, die sie benötigen.  Klicken Sie auf Herunterfahren werden diese Informationen nicht benötigt.  `IVsTrackProjectDocuments2` wird von <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>bereitgestellt.  
  
 Für jedes Hinzufügen, Umbenennen und Entfernen von Aktion, es gibt eine `OnQuery*`\-Methode und eine `OnAfter*`\-Methode.  Rufen Sie die `OnQuery*`\-Methode auf, um die Berechtigungen anzufordern die Datei oder das Verzeichnis hinzuzufügen, umbenennen oder entfernen.  Rufen Sie die `OnAfter*`\-Methode nach der Datei oder das aktuelle Verzeichnis wurde hinzugefügt, entfernt oder umbenannt und der Zustand gibt den neuen Zustand.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [Unterstützung von Datenquellen\-Steuerelement](../../extensibility/internals/supporting-source-control.md)
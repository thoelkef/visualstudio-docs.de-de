---
title: "Vereinfachen des Einbettens | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK], Benutzerdefiniert - einfache anzeigen einbetten"
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Vereinfachen des Einbettens
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vereinfachte Einbettung ist in einem Editor aktiviert sein, wenn die Dokumente Objekt ist \(d. h. ein untergeordnetes Element\), [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]gemachte untergeordnet, und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>\-Schnittstelle wird implementiert, um die zugehörigen Befehle Fenster zu behandeln.  Vereinfacht kann das Einbetten von Editoren keine aktive Steuerelemente des Hosts.  Die Objekte, die verwendet werden, um einen Editor mit vereinfachter Einbettung zu erstellen, werden in der folgenden Abbildung gezeigt.  
  
 ![Grafik zum vereinfachten Einbettungs&#45;Editor](../extensibility/media/vssimplifiedembeddingeditor.png "vsSimplifiedEmbeddingEditor")  
Editor mit dem Einbetten vereinfachter  
  
> [!NOTE]
>  Von den Objekten in dieser Abbildung lediglich das `CYourEditorFactory`\-Objekt ist erforderlich, um einen dateibasierten StandardEditor zu erstellen.  Wenn Sie einen benutzerdefinierten Editor erstellen, ist es nicht erforderlich, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>zu implementieren, da sich der Editor über einen eigenen privaten Mechanismus zur Beibehaltung.  Für gewohnheit Editoren Sie müssen jedoch nicht.  
  
 Alle Schnittstellen, die implementiert werden, um einen Editor mit vereinfachter Einbettung zu erstellen, werden im `CYourEditorDocument`\-Objekt enthalten.  Um mehrere Ansichten von Dokumenten von Daten zu unterstützen, weisen Sie die Schnittstellen für separate Daten und Objekte, wie in der folgenden Tabelle angegeben.  
  
|Schnittstelle|Speicherort der Schnittstelle|Verwendung|  
|-------------------|-----------------------------------|----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Ansicht|Stellt eine Verbindung mit dem übergeordneten Fenster.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Ansicht|Behandelt Befehle.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Ansicht|Aktiviert Statusleisten aktualisiert.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Ansicht|Aktiviert Toolboxelemente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Daten|Sendet Benachrichtigungen, wenn die Datei geändert wird.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Daten|Aktiviert das Feature für einen Dateityp.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Daten|Aktiviert die Persistenz für das Dokument.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Daten|Ermöglicht die Änderung der Datei Unterdrückung von Ereignissen, z. B. Reload starten.|
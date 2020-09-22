---
title: Vereinfachte Einbettung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b8e1ac2fa17409ac3228f87eb71c99ce9e725521
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840850"
---
# <a name="simplified-embedding"></a>Vereinfachtes Einbetten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vereinfachte Einbettungen werden in einem Editor aktiviert, wenn das Dokument Ansichts Objekt (d. h. ein untergeordnetes Element von) übergeordnet ist [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , und die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle wird implementiert, um Ihre Fenster Befehle zu verarbeiten. Vereinfachte Einbettungs Editoren können keine aktiven Steuerelemente hosten Die Objekte, die zum Erstellen eines Editors mit vereinfachter Einbettung verwendet werden, sind in der folgenden Abbildung dargestellt.  
  
 ![Grafik zum vereinfachten Einbettungs-Editor](../extensibility/media/vssimplifiedembeddingeditor.gif "vssimplifiedembeddingeditor")  
Editor mit vereinfachter Einbettung  
  
> [!NOTE]
> Von den Objekten in dieser Abbildung ist nur das- `CYourEditorFactory` Objekt zum Erstellen eines standardmäßigen dateibasierten Editors erforderlich. Wenn Sie einen benutzerdefinierten Editor erstellen, müssen Sie nicht implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> , da Ihr Editor wahrscheinlich über einen eigenen Mechanismus für die private Persistenz verfügt. Für Nichtbenutzer definierte Editoren müssen Sie dies jedoch tun.  
  
 Alle Schnittstellen, die zum Erstellen eines Editors mit vereinfachter Einbettung implementiert werden, sind im- `CYourEditorDocument` Objekt enthalten. Wenn Sie jedoch mehrere Sichten von Dokument Daten unterstützen möchten, teilen Sie die Schnittstellen auf separate Daten und Objekte anzeigen, wie in der folgenden Tabelle aufgeführt.  
  
|Schnittstelle|Speicherort der Schnittstelle|Verwendung|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Ansicht|Stellt eine Verbindung mit dem übergeordneten Fenster bereit.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Ansicht|Behandelt Befehle.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Ansicht|Ermöglicht Aktualisierungen der Statusleiste.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Ansicht|Aktiviert **Toolbox** Elemente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Daten|Sendet Benachrichtigungen, wenn die Datei geändert wird.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Daten|Aktiviert das Feature "Speichern unter" für einen Dateityp.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Daten|Aktiviert die Persistenz für das Dokument.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Daten|Ermöglicht die Unterdrückung von Datei Änderungs Ereignissen, z. b. das Auslösen von Neuladen.|

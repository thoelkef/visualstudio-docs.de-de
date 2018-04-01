---
title: Einbetten von vereinfacht | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 16
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 183dc4ad9d7ea1a2f6855be050ad8459a3f801ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="simplified-embedding"></a>Einbetten von vereinfacht
Vereinfachte Einbetten in einem Editor aktiviert ist, wenn seine dokumentansichtsobjekts übergeordnet ist (d. h. ein untergeordnetes Element des vorgenommen) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle wird implementiert, um die Befehle "Fenster" zu behandeln. Vereinfachte Einbetten von Editoren können keine aktive Steuerelemente hosten. Beim Erstellen eines Editors mit vereinfachten einbetten verwendeten Objekte sind in der folgenden Abbildung gezeigt.  
  
 ![Vereinfachten Einbettungs-Editor-Grafik](../extensibility/media/vssimplifiedembeddingeditor.gif "VsSimplifiedEmbeddingEditor")  
-Editor mit vereinfachten einbetten  
  
> [!NOTE]
>  Der Objekte in dieser Abbildung bietet nur die `CYourEditorFactory` Objekt ist erforderlich, um einen standardmäßigen dateibasierten-Editor zu erstellen. Wenn Sie einen benutzerdefinierten Editor erstellen, müssen Sie nicht implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, da Ihr Editor wahrscheinlich einen eigenen Mechanismus für die dauerhafte Speicherung verfügt. Für nicht benutzerdefinierte Editoren aber müssen Sie.  
  
 Alle Schnittstellen implementiert, um das Erstellen eines Editors mit vereinfachten einbetten enthalten sind, der `CYourEditorDocument` Objekt. Jedoch zur Unterstützung von mehreren Ansichten der Dokumentdaten unterteilt werden die Schnittstellen auf separaten Daten und Ansicht-Objekte in der folgenden Tabelle aufgeführt.  
  
|Interface|Speicherort der-Schnittstelle|Mit|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Ansicht|Stellt die Verbindung mit dem übergeordneten Fenster.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Ansicht|Befehle behandelt.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Ansicht|Ermöglicht Aktualisierungen der Statusleiste.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Ansicht|Ermöglicht **Toolbox** Elemente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Daten|Sendet Benachrichtigungen, wenn die Datei geändert wird.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Daten|Aktiviert die Funktion "Speichern unter" für einen Dateityp an.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Daten|Aktiviert die Persistenz für das Dokument.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Daten|Ermöglicht die Unterdrückung der Änderungsereignisse für Datei, z. B. zum erneuten Laden auslösen.|
---
title: Zum Vereinfachen des Einbettens | Microsoft-Dokumentation
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
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e59e09f475697ac0539384514837554e3ce85afc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736227"
---
# <a name="simplified-embedding"></a>Vereinfachtes Einbetten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vereinfachtes Einbetten in einem Editor aktiviert ist, wenn die dokumentenansichtsobjekt untergeordnet ist (d. h. ein untergeordnetes Element des vorgenommen) [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle wird implementiert, um die Befehle im Fenster zu behandeln. Vereinfachte einbettende Editoren können keine aktive Steuerelemente hosten. Beim Erstellen eines Editors vereinfachtes einbetten verwendeten Objekte werden in der folgenden Abbildung angezeigt.  
  
 ![Vereinfachten Einbettungs-Editor-Grafik](../extensibility/media/vssimplifiedembeddingeditor.gif "VsSimplifiedEmbeddingEditor")  
Editor für vereinfachtes einbetten  
  
> [!NOTE]
>  Der Objekte in dieser Abbildung ist nur der `CYourEditorFactory` ist erforderlich, um einen Standardeditor für dateibasierte zu erstellen. Wenn Sie einen benutzerdefinierten Editor erstellen, Sie müssen keine implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>, da Ihr Editor wahrscheinlich einen eigenen Mechanismus für die dauerhafte Speicherung verfügt. Für nicht benutzerdefinierte Editoren aber müssen Sie.  
  
 Alle Schnittstellen implementiert, um das Erstellen eines Editors vereinfachtes einbetten befinden sich die `CYourEditorDocument` Objekt. Jedoch zur Unterstützung von mehreren Ansichten der Dokumentdaten unterteilt die Schnittstellen auf separaten Daten und Ansicht-Objekten in der folgenden Tabelle aufgeführt.  
  
|Interface|Speicherort der-Schnittstelle|Mit|  
|---------------|---------------------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Ansicht|Verbindung mit dem übergeordneten Fenster bereitstellt.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Ansicht|Befehle behandelt.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Ansicht|Ermöglicht Aktualisierungen der Statusleiste.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Ansicht|Ermöglicht **Toolbox** Elemente.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Daten|Sendet Benachrichtigungen, wenn die Datei geändert wird.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Daten|Aktiviert die Funktion "Speichern unter" für einen Dateityp.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Daten|Aktiviert die Persistenz für das Dokument.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Daten|Ermöglicht die Unterdrückung der Änderungsereignisse für Datei, wie das erneute Laden auslösen.|


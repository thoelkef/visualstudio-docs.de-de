---
title: Vereinfachte Einbettung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - simple view embedding
ms.assetid: f1292478-a57d-48ec-8c9e-88a23f04ffe5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9bc9619ae1ed75aed3656ff014296f7c7d88fa0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700076"
---
# <a name="simplified-embedding"></a>Vereinfachtes Einbetten
Die vereinfachte Einbettung ist in einem Editor aktiviert, wenn das Dokumentansichtsobjekt zu (d. h. zu einem untergeordneten Element) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]übergeordnet ist und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> Schnittstelle implementiert wird, um ihre Fensterbefehle zu verarbeiten. Vereinfachte Einbettungseditoren können keine aktiven Steuerelemente hosten. Die Objekte, die zum Erstellen eines Editors mit vereinfachter Einbettung verwendet werden, sind in der folgenden Abbildung dargestellt.

 ![Vereinfachte Einbettungs-Editor-Grafik](../extensibility/media/vssimplifiedembeddingeditor.gif "vsSimplifiedEmbeddingEditor") Editor mit vereinfachter Einbettung

> [!NOTE]
> Von den Objekten in dieser `CYourEditorFactory` Abbildung ist nur das Objekt erforderlich, um einen dateibasierten Standardeditor zu erstellen. Wenn Sie einen benutzerdefinierten Editor erstellen, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>müssen Sie nicht implementieren, da der Editor wahrscheinlich über einen eigenen privaten Persistenzmechanismus verfügt. Für nicht benutzerdefinierte Editoren müssen Sie dies jedoch tun.

 Alle Schnittstellen, die zum Erstellen eines Editors mit `CYourEditorDocument` vereinfachter Einbettung implementiert sind, sind im Objekt enthalten. Um jedoch mehrere Ansichten von Dokumentdaten zu unterstützen, teilen Sie die Schnittstellen in separate Daten auf und zeigen Sie Objekte an, wie in der folgenden Tabelle angegeben.

|Schnittstelle|Position der Schnittstelle|Zweck|
|---------------|---------------------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Ansicht|Stellt eine Verbindung zum übergeordneten Fenster bereit.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Ansicht|Behandelt Befehle.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>|Ansicht|Ermöglicht Aktualisierungen der Statusleiste.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser>|Ansicht|Aktiviert **Toolbox-Elemente.**|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEvents>|Daten|Sendet Benachrichtigungen, wenn sich die Datei ändert.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>|Daten|Aktiviert das Feature Speichern unter für einen Dateityp.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>|Daten|Aktiviert die Persistenz für das Dokument.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl>|Daten|Ermöglicht die Unterdrückung von Dateiänderungsereignissen, z. B. das Auslösen von Neuladeereignissen.|

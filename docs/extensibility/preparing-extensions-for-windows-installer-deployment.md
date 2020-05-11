---
title: Vorbereiten von Erweiterungen für die Windows Installer-Bereitstellung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8636dfbbad06192e5edbb61a9a784f64b8f3f14f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702026"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Vorbereiten von Erweiterungen für die Windows Installer-Bereitstellung
Sie können kein Windows Installer-Paket (MSI) verwenden, um ein VSIX-Paket bereitzustellen. Sie können jedoch den Inhalt eines VSIX-Pakets für die MSI-Bereitstellung extrahieren. Dieses Dokument zeigt, wie Sie ein Projekt vorbereiten, dessen Standardausgabe ein VSIX-Paket für die Aufnahme in ein Setupprojekt ist.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Vorbereiten eines Erweiterungsprojekts für die Windows Installer-Bereitstellung
 Führen Sie diese Schritte für neue Erweiterungsprojekte aus, bevor Sie einem Setupprojekt hinzufügen.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>So bereiten Sie ein Erweiterungsprojekt für die Windows Installer-Bereitstellung vor

1. Erstellen Sie ein VSPackage, eine MEF-Komponente, einen Editor-Adornment oder einen anderen Erweiterbarkeitsprojekttyp, der ein VSIX-Manifest enthält.

2. Öffnen Sie das VSIX-Manifest im Code-Editor.

3. Legen `InstalledByMsi` Sie das Element des `true`VSIX-Manifests auf fest. Weitere Informationen zum VSIX-Manifest finden Sie unter [VSIX-Erweiterungsschema 2.0-Referenz](../extensibility/vsix-extension-schema-2-0-reference.md).

     Dadurch wird verhindert, dass das VSIX-Installationsprogramm versucht, die Komponente zu installieren.

4. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Eigenschaften**.

5. Wählen Sie die Registerkarte **VSIX** aus.

6. Aktivieren Sie das Kontrollkästchen **VSIX-Inhalt kopieren an den folgenden Speicherort,** und geben Sie den Pfad ein, zu dem das Setupprojekt die Dateien abholt.

## <a name="extract-files-from-an-existing-vsix-package"></a>Extrahieren von Dateien aus einem vorhandenen VSIX-Paket
 Führen Sie diese Schritte aus, um den Inhalt eines vorhandenen VSIX-Pakets zu einem Setup-Projekt hinzuzufügen, wenn Sie nicht über die Quelldateien verfügen.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>So extrahieren Sie Dateien aus einem vorhandenen VSIX-Paket

1. Benennen Sie die *um. VSIX-Datei* mit der Erweiterung von *filename.vsix* zu *filename.zip*.

2. Kopieren Sie den Inhalt der *ZIP-Datei* in ein Verzeichnis.

3. Löschen Sie die Datei *[Content_types].xml* aus dem Verzeichnis.

4. Bearbeiten Sie das VSIX-Manifest, wie im vorherigen Verfahren gezeigt.

5. Fügen Sie die verbleibenden Dateien zu Ihrem Setup-Projekt hinzu.

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Installationsprogrammbereitstellung](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Aktion](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))

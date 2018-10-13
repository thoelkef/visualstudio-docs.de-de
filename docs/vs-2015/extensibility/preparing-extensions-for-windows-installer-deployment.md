---
title: Vorbereiten von Erweiterungen für Windows Installer-Bereitstellung | Microsoft-Dokumentation
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
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4483fef9c200f6814c247f14ee956bfef4582e6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197924"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Vorbereiten von Erweiterungen für die Windows Installer-Bereitstellung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein Windows Installer-Paket (MSI) können Sie ein VSIX-Paket bereitstellen. Allerdings können Sie den Inhalt einer VSIX-Pakets für die Bereitstellung der MSI-Datei extrahieren. Diesem Dokument wird erläutert, wie Sie ein Projekt vorbereiten, deren Standardausgabe ein VSIX-Paket für die Aufnahme in ein Setup-Projekt ist.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Vorbereiten von ein Projekt für die Windows Installer-Bereitstellung  
 Führen Sie diese Schritte können Sie neue Erweiterung-Projekte aus, bevor Sie ein Setup-Projekt hinzufügen.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>So bereiten Sie ein Erweiterungsprojekt für Windows Installer-Bereitstellung vor  
  
1.  Erstellen Sie ein VSPackage, MEF-Komponente, Editor Zusatzelement oder anderen Projekttyp für Erweiterbarkeit, die einem VSIX-Manifest enthält.  
  
2.  Öffnen Sie das VSIX-Manifest im Code-Editor ein.  
  
3.  Legen Sie das InstalledByMsi-Element des VSIX-Manifests, das `true`. Weitere Informationen zu VSIX-Manifest, finden Sie unter [Referenz zum VSIX-Erweiterungsschema 2.0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Dadurch wird verhindert, dass das VSIX-Installationsprogramm die Komponente installieren möchten.  
  
4.  Mit der rechten Maustaste in des Projekts im **Projektmappen-Explorer** , und klicken Sie auf **Eigenschaften**.  
  
5.  Wählen Sie die **VSIX** Registerkarte.  
  
6.  Aktivieren Sie das Kontrollkästchen mit der Bezeichnung **Kopie VSIX-Inhalt am folgenden Speicherort** , und geben Sie den Pfad zur, in dem das Setup-Projekt die Dateien abruft.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Extrahieren von Dateien aus einem vorhandenen VSIX-Paket  
 Führen Sie diese Schritte aus, um den Inhalt eines vorhandenen VSIX-Pakets zu einem Setupprojekt hinzufügen, wenn Sie nicht über die Quelldateien verfügen.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Um Dateien aus einem vorhandenen VSIX-Paket zu extrahieren.  
  
1.  Benennen Sie die. VSIX-Datei, die mit der Erweiterung *Filename*.vsix um *Filename*ZIP.  
  
2.  Kopieren Sie den Inhalt der ZIP-Datei in ein Verzeichnis an.  
  
3.  Löschen Sie die [Content_types] .xml-Datei aus dem Verzeichnis ein.  
  
4.  Bearbeiten Sie das VSIX-Manifest aus, wie im vorherigen Verfahren dargestellt.  
  
5.  Fügen Sie die restlichen Dateien zu Ihrem Setup-Projekt hinzu.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Installer-Bereitstellung](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Aktion](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)


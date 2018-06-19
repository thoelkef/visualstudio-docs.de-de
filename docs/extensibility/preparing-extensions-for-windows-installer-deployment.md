---
title: Vorbereiten von Erweiterungen für Windows Installer-Bereitstellung | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef51b3cb0f84a470f104ff688c1149e607d16f71
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136325"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Vorbereiten von Erweiterungen für Windows Installer-Bereitstellung
Sie können keine Windows Installer-Paket (MSI) verwenden, um ein VSIX-Paket bereitzustellen. Allerdings können Sie den Inhalt eines VSIX-Pakets für die Bereitstellung der MSI-Datei extrahieren. Dieses Dokument zeigt, wie ein Projekt vorbereitet, deren Standardausgabe ein VSIX-Paket für die Aufnahme in ein Setup-Projekt ist.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Vorbereitung der Windows Installer-Bereitstellung ein Erweiterungsprojekt  
 Führen Sie diese Schritte auf neue Erweiterungsprojekten vor dem Setup-Projekt hinzufügen.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>So bereiten Sie ein Erweiterungsprojekt für Windows Installer-Bereitstellung vor  
  
1.  Erstellen Sie ein VSPackage, MEF-Komponente, Editor Zusatzelement (adornment) oder anderer Erweiterbarkeit-Projekttyp, der ein VSIX-Manifest enthält.  
  
2.  Öffnen Sie das VSIX-Manifest in Code-Editor.  
  
3.  Legen Sie die InstalledByMsi Element des VSIX-Manifests, um `true`. Weitere Informationen über das VSIX-Manifest finden Sie unter [VSIX-Erweiterung 2.0 Schemareferenz](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Dadurch wird verhindert, dass das VSIX-Installationsprogramm versucht, die Komponente zu installieren.  
  
4.  Mit der rechten Maustaste des Projekts im **Projektmappen-Explorer** , und klicken Sie auf **Eigenschaften**.  
  
5.  Wählen Sie die **VSIX** Registerkarte.  
  
6.  Aktivieren Sie das Kontrollkästchen mit der Bezeichnung **Kopie VSIX-Inhalt an folgendem Ort** und geben Sie den Pfad an, in dem das Setup-Projekt die Dateien abruft.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Extrahieren von Dateien aus einer vorhandenen VSIX-Paket  
 Führen Sie diese Schritte aus, um den Inhalt eines vorhandenen VSIX-Pakets zu einem Setupprojekt hinzufügen, wenn Sie nicht über die Quelldateien verfügen.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Zum Extrahieren von Dateien aus einer vorhandenen VSIX-Paket  
  
1.  Benennen Sie die. VSIX-Datei, die mit der Erweiterung auf *Filename*.vsix um *Filename*ZIP.  
  
2.  Kopieren Sie den Inhalt der ZIP-Datei in ein Verzeichnis an.  
  
3.  Löschen Sie die [Content_types] .xml-Datei aus dem Verzeichnis ein.  
  
4.  Bearbeiten Sie die VSIX-Manifest an, wie in der vorherigen Prozedur beschrieben.  
  
5.  Die restlichen Dateien dem Setup-Projekt hinzufügen.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio Installer-Bereitstellung](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Aktion](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)
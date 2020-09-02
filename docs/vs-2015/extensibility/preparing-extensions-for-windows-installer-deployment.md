---
title: Vorbereiten von Erweiterungen für Windows Installer Bereitstellung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 76d7f879fade99914bf3f56ade0ec1270e14f4c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694596"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Vorbereiten von Erweiterungen für die Windows Installer-Bereitstellung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zum Bereitstellen eines VSIX-Pakets können Sie kein Windows Installer Paket (MSI) verwenden. Sie können jedoch den Inhalt eines VSIX-Pakets für die MSI-Bereitstellung extrahieren. In diesem Dokument wird gezeigt, wie ein Projekt vorbereitet wird, dessen Standardausgabe ein VSIX-Paket für die Einbindung in ein Setup-Projekt ist.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Vorbereiten eines Erweiterungsprojekts für Windows Installer Bereitstellung  
 Führen Sie diese Schritte für neue Erweiterungsprojekte aus, bevor Sie Sie einem Setup-Projekt hinzufügen.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>So bereiten Sie ein Erweiterungsprojekt für Windows Installer Bereitstellung vor  
  
1. Erstellen Sie ein VSPackage, eine MEF-Komponente, ein Editor-Adornment oder einen anderen Erweiterbarkeits Projekttyp, der ein VSIX-Manifest enthält.  
  
2. Öffnen Sie im Code-Editor das VSIX-Manifest.  
  
3. Legen Sie das InstalledByMSI-Element des VSIX-Manifests auf fest `true` . Weitere Informationen zum VSIX-Manifest finden Sie in der [Referenz zu VSIX-Erweiterungs Schema 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Dadurch wird verhindert, dass der VSIX-Installer versucht, die Komponente zu installieren.  
  
4. Klicken Sie mit der rechten Maustaste **Projektmappen-Explorer** auf das Projekt, und klicken Sie auf **Eigenschaften**  
  
5. Wählen Sie die Registerkarte **VSIX** aus.  
  
6. Aktivieren Sie das Kontrollkästchen **VSIX-Inhalt kopieren an den folgenden Speicherort,** und geben Sie den Pfad ein, in den die Dateien vom Setup-Projekt übernommen werden.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Extrahieren von Dateien aus einem vorhandenen VSIX-Paket  
 Führen Sie diese Schritte aus, um den Inhalt eines vorhandenen VSIX-Pakets zu einem Setup-Projekt hinzuzufügen, wenn Sie nicht über die Quelldateien verfügen.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>So extrahieren Sie Dateien aus einem vorhandenen VSIX-Paket  
  
1. Benennen Sie den um. VSIX-Datei, die die Erweiterung von *Dateiname*. vsix zu *filename*. zip enthält.  
  
2. Kopieren Sie den Inhalt der ZIP-Datei in ein Verzeichnis.  
  
3. Löschen Sie die Datei [Content_Types]. XML aus dem Verzeichnis.  
  
4. Bearbeiten Sie das VSIX-Manifest, wie in der vorherigen Prozedur gezeigt.  
  
5. Fügen Sie die verbleibenden Dateien dem Setup-Projekt hinzu.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Visual Studio-Installer Bereitstellung](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Exemplarische Vorgehensweise: Erstellen einer benutzerdefinierten Aktion](https://msdn.microsoft.com/4bd4b63a-2b91-431e-839c-5752443f0eaf)

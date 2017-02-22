---
title: "Vorbereiten von Erweiterungen f&#252;r Windows Installer-Bereitstellung | Microsoft Docs"
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
  - "VSIX-MSI-Datei"
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Vorbereiten von Erweiterungen f&#252;r Windows Installer-Bereitstellung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Windows Installer\-Paket \(MSI\) können Sie ein VSIX\-Paket bereitstellen. Allerdings können Sie den Inhalt eines VSIX\-Pakets für die Bereitstellung der MSI\-Datei extrahieren. Dieses Dokument zeigt, wie Sie ein Projekt vorbereiten, deren Standardausgabe ein VSIX\-Paket für die Aufnahme in ein Setup\-Projekt ist.  
  
## Vorbereitung der Bereitstellung von Windows Installer ein Erweiterungsprojekt  
 Diese Schritte auf neuen Projekten ausgeführt, bevor Sie ein Setup\-Projekt hinzufügen.  
  
#### So bereiten Sie ein Erweiterungsprojekt für Windows Installer\-Bereitstellung vor  
  
1.  Erstellen Sie ein VSPackage, MEF\-Komponente, Editor Adornment oder andere Erweiterbarkeit\-Projekttyp, der eine VSIX\-Manifest enthält.  
  
2.  Öffnen Sie das VSIX\-Manifest im Code\-Editor.  
  
3.  Legen Sie das Element InstalledByMsi des VSIX\-Manifest `true`. Weitere Informationen über das VSIX\-Manifest finden Sie unter [VSIX\-Erweiterung Schemareferenz 2.0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Dadurch wird verhindert, dass das VSIX\-Installationsprogramm versucht, die Komponente zu installieren.  
  
4.  Mit der rechten Maustaste des Projekts im **Projektmappen\-Explorer** und klicken Sie auf **Eigenschaften**.  
  
5.  Wählen Sie die **VSIX** Registerkarte.  
  
6.  Aktivieren Sie das Kontrollkästchen mit der Bezeichnung **Kopie VSIX\-Inhalt an den folgenden Speicherort** und geben Sie den Pfad, in dem das Setup\-Projekt die Dateien abruft.  
  
## Extrahieren von Dateien aus einer vorhandenen VSIX\-Paket  
 Führen Sie diese Schritte, um den Inhalt eines vorhandenen VSIX\-Pakets ein Setup\-Projekt hinzufügen, wenn Sie nicht über die Quelldateien verfügen.  
  
#### Zum Extrahieren von Dateien aus einer vorhandenen VSIX\-Paket  
  
1.  Benennen Sie die. VSIX\-Datei mit der Erweiterung *Dateiname*VSIX zu *Dateiname*ZIP.  
  
2.  Kopieren Sie den Inhalt der ZIP\-Datei in ein Verzeichnis.  
  
3.  Löschen Sie die \[Content\_types\] .xml\-Datei aus dem Verzeichnis.  
  
4.  Bearbeiten Sie das VSIX\-Manifest, wie im vorherigen Verfahren dargestellt.  
  
5.  Fügen Sie die restlichen Dateien zum Setup\-Projekt hinzu.  
  
## Siehe auch  
 [Visual Studio Installer Deployment](http://msdn.microsoft.com/de-de/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Walkthrough: Creating a Custom Action](http://msdn.microsoft.com/de-de/4bd4b63a-2b91-431e-839c-5752443f0eaf)
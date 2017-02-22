---
title: "Gewusst wie: hinzuf&#252;gen eine Abh&#228;ngigkeit zu einem VSIX-Paket | Microsoft Docs"
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
  - "Paket-Referenz"
  - "Paket-assembly"
  - "Paket-dll"
  - "VSIX-Referenz"
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: hinzuf&#252;gen eine Abh&#228;ngigkeit zu einem VSIX-Paket
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können ein VSIX\-Paket\-Bereitstellung einrichten, die alle Abhängigkeiten installiert, die nicht bereits auf dem Zielcomputer vorhanden sind. Um dies zu erreichen, enthalten Sie die VSIX\-Abhängigkeiten zu der Datei "Source.Extension.vsixmanifest".  
  
#### Zum Hinzufügen einer Abhängigkeit  
  
1.  Öffnen Sie die Datei "Source.Extension.vsixmanifest" in der **Design** anzeigen. Klicken Sie auf die **Abhängigkeiten** Registerkarte, und klicken Sie auf **Neu**.  
  
2.  Zum Hinzufügen einer installierten Erweiterung: in der **neue Abhängigkeit hinzufügen** wählen Sie im Dialogfeld **Erweiterung installiert** und schließlich für den **Namen**, Erweiterung in der Liste auswählen.  
  
3.  Eine andere VSIX hinzufügen, die nicht installiert ist:: in der **neue Abhängigkeit hinzufügen** wählen Sie im Dialogfeld **Dateisystem** und verwenden Sie dann die **Durchsuchen** klicken, um der VSIX\-Datei auszuwählen.  
  
## Siehe auch  
 [VSIX\-Erweiterung Schemareferenz 1.0](http://msdn.microsoft.com/de-de/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Anatomie eines VSIX\-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [Vorbereiten von Erweiterungen für Windows Installer\-Bereitstellung](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
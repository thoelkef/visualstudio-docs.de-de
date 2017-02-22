---
title: "How to: Set a Custom Log File Location for ClickOnce Deployment Errors | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "troubleshooting ClickOnce deployments"
  - "ClickOnce deployment, troubleshooting"
  - "ClickOnce deployment, error logging"
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Set a Custom Log File Location for ClickOnce Deployment Errors
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwaltet Aktivierungsprotokolldateien für alle Bereitstellungen.  Diese Protokolle dokumentieren alle Fehler, die das Installieren und das Initialisieren einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung betreffen.  Standardmäßig erstellt [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] eine Protokolldatei für jede Bereitstellungsaktivierung.  Es speichert diese Protokolldateien im Ordner Temporäre Internetdateien.  Die Protokolldatei für eine Bereitstellung wird angezeigt, wenn ein Fehler bei der Aktivierung auftritt und in dem daraufhin angezeigten Fehlerdialogfeld auf **Details** geklickt wird.  
  
 Sie können dieses Verhalten für einen bestimmten Client ändern und dazu mit dem Registrierungs\-Editor \(**regedit.exe**\) einen benutzerdefinierten Protokolldateipfad festlegen.  In diesem Fall protokolliert [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] erfolgreiche und nicht erfolgreiche Aktivierungen für alle Bereitstellungen in einer einzelnen Datei.  
  
> [!CAUTION]
>  Die unsachgemäße Verwendung des Registrierungs\-Editors kann ernste Probleme verursachen und u. U. eine Neuinstallation des Betriebssystems erforderlich machen.  Die Verwendung des Registrierungs\-Editors erfolgt auf eigenes Risiko.  
  
> [!NOTE]
>  Sie müssen die Protokolldatei gelegentlich verkürzen oder löschen, damit sie nicht zu groß wird.  
  
 Im folgenden Verfahren wird beschrieben, wie ein benutzerdefinierter Protokolldateispeicherort für einen einzelnen Client festgelegt wird.  
  
### So legen Sie einen benutzerdefinierten Protokolldateispeicherort fest  
  
1.  Öffnen Sie **Regedit.exe**.  
  
2.  Navigieren Sie zum Knoten `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Legen Sie für den Zeichenfolgenwert `LogFilePath` den vollständigen Pfad und Dateinamen des von Ihnen bevorzugten benutzerdefinierten Protokollspeicherorts fest.  
  
     Dieser Speicherort muss in einem Verzeichnis sein, auf das Benutzer Schreibzugriff haben.  Erstellen Sie unter Windows Vista z. B. die folgende Ordnerstruktur, und legen Sie `LogFilePath` auf "C:\\Users\\\<Benutzername\>\\Documents\\Logs\\ClickOnce\\installation.log" fest.  
  
## Siehe auch  
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)
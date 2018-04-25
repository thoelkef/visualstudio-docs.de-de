---
title: 'Vorgehensweise: Festlegen einer benutzerdefinierten Protokolldateispeicherorts für ClickOnce-Bereitstellungsfehler | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 647eed5145d9d80f9fc62249763726a5940a7345
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Gewusst wie: Festlegen eines benutzerdefinierten Protokolldateispeicherorts für ClickOnce-Bereitstellungsfehler
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwaltet die Aktivierung von Protokolldateien für alle Bereitstellungen an. Diese Protokolle dokumentieren Fehler bezieht sich auf installieren, und Initialisieren einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung. Standardmäßig [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] erstellt eine einzige Protokolldatei für jede Bereitstellung-Aktivierung. Sie speichert diese Protokolldateien im Ordner "temporäre Internetdateien". Die Protokolldatei für eine Bereitstellung wird dem Benutzer angezeigt, wenn ein Aktivierungsfehler tritt auf, und der Benutzer klickt auf **Details** im Dialogfeld resultierenden Fehler.  
  
 Sie können dieses Verhalten für einen bestimmten Client ändern, indem Sie mithilfe des Registrierungs-Editor (**regedit.exe**) einen benutzerdefinierten Protokollpfad Datei festlegen. In diesem Fall [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Aktivierung Erfolge und Fehler für alle Bereitstellungen in einer einzelnen Datei protokolliert.  
  
> [!CAUTION]
>  Falsch Verwendung des Registrierungs-Editors können zu schwerwiegende Problemen führen, die möglicherweise eine Neuinstallation des Betriebssystems erforderlich sind. Sie verwenden den Registrierungs-Editor auf eigene Gefahr.  
  
> [!NOTE]
>  Sie benötigen zum Abschneiden oder löschen die Protokolldatei gelegentlich, um zu verhindern, dass es zu groß.  
  
 Das folgende Verfahren beschreibt, wie einem benutzerdefinierten Protokolldateispeicherorts für einen einzelnen Client festgelegt.  
  
### <a name="to-set-a-custom-log-file-location"></a>Festlegen einer benutzerdefinierten Protokolldateispeicherorts  
  
1.  Open **Regedit.exe**.  
  
2.  Navigieren Sie zum Knoten `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Legen Sie den Zeichenfolgenwert `LogFilePath` auf den vollständigen Pfad und Dateiname der Ihre bevorzugte benutzerdefinierten Protokollspeicherort.  
  
     Dieser Speicherort muss sich in einem Verzeichnis auf die der Benutzer Schreibzugriff hat. Beispielsweise unter Windows Vista, erstellen Sie die folgende Ordnerstruktur und die legen `LogFilePath` zu C:\Users\\< Benutzername\>\Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)
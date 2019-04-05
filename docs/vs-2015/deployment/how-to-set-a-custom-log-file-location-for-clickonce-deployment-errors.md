---
title: 'Vorgehensweise: Festlegen ein benutzerdefinierten Protokolldateispeicherorts für ClickOnce-Bereitstellungsfehler | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a38e453d9bfff3b2633eb98cc5d6127fa126335f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961464"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Vorgehensweise: Festlegen eines benutzerdefinierten Protokolldateispeicherorts für ClickOnce-Bereitstellungsfehler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] verwaltet die Aktivierung von Protokolldateien für alle Bereitstellungen. Diese Protokolle enthalten Fehler in Bezug auf Installieren und initialisieren eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung. In der Standardeinstellung [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] erstellt eine Protokolldatei für jede Bereitstellung-Aktivierung. Diese Protokolldateien im Ordner "temporäre Internetdateien" gespeichert. Die Protokolldatei für eine Bereitstellung wird für den Benutzer angezeigt, wenn ein Aktivierungsfehler tritt auf, und der Benutzer klickt auf **Details** im daraufhin angezeigten Fehlerdialogfeld.  
  
 Sie können dieses Verhalten für einen bestimmten Client ändern, indem Sie mithilfe des Registrierungs-Editor (**regedit.exe**) um einen benutzerdefinierten Protokollpfad Datei festzulegen. In diesem Fall [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Activation-Erfolge und Fehler für alle Bereitstellungen in einer einzelnen Datei protokolliert.  
  
> [!CAUTION]
>  Wenn Sie den Registrierungs-Editor nicht ordnungsgemäß verwenden, können Sie schwerwiegenden Problemen führen, die Neuinstallation des Betriebssystems erforderlich machen können. Sie verwenden den Registrierungs-Editor auf eigene Gefahr.  
  
> [!NOTE]
>  Sie benötigen zum Abschneiden oder löschen die Protokolldatei gelegentlich, um zu verhindern, dass es zu groß.  
  
 Das folgende Verfahren beschreibt das Festlegen ein benutzerdefinierten Protokolldateispeicherorts für einen einzelnen Client.  
  
### <a name="to-set-a-custom-log-file-location"></a>Festlegen ein benutzerdefinierten Protokolldateispeicherorts  
  
1.  Open **Regedit.exe**.  
  
2.  Navigieren Sie zum Knoten `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  Legen Sie den Zeichenfolgenwert `LogFilePath` auf den vollständigen Pfad und Dateiname der Ihre bevorzugte benutzerdefinierten Protokollspeicherort.  
  
     Dieser Speicherort muss sich in einem Verzeichnis auf die der Benutzer Schreibzugriff hat. Beispielsweise unter Windows Vista, erstellen Sie die folgende Ordnerstruktur und die legen `LogFilePath` zu C:\Users\\< Benutzername\>\Documents\Logs\ClickOnce\installation.log.  
  
## <a name="see-also"></a>Siehe auch  
 [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)

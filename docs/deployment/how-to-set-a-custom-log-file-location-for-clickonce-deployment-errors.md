---
title: Festlegen von benutzerdefinierten Protokolldateispeicherorts für ClickOnce bereitstellen, Fehler
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbfdbb73d7b7cc1e3dc92e59a1c0dd8d5093269e
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263230"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Vorgehensweise: Festlegen eines benutzerdefinierten Protokolldateispeicherorts für ClickOnce-Bereitstellungsfehler
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verwaltet die Aktivierung von Protokolldateien für alle Bereitstellungen. Diese Protokolle enthalten Fehler in Bezug auf Installieren und initialisieren eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung. In der Standardeinstellung [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] erstellt eine Protokolldatei für jede Bereitstellung-Aktivierung. Diese Protokolldateien im Ordner "temporäre Internetdateien" gespeichert. Die Protokolldatei für eine Bereitstellung wird für den Benutzer angezeigt, wenn ein Aktivierungsfehler tritt auf, und der Benutzer klickt auf **Details** im daraufhin angezeigten Fehlerdialogfeld.

 Sie können dieses Verhalten für einen bestimmten Client ändern, indem Sie mithilfe des Registrierungs-Editor (**regedit.exe**) um einen benutzerdefinierten Protokollpfad Datei festzulegen. In diesem Fall [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Activation-Erfolge und Fehler für alle Bereitstellungen in einer einzelnen Datei protokolliert.

> [!CAUTION]
> Wenn Sie den Registrierungs-Editor nicht ordnungsgemäß verwenden, können Sie schwerwiegenden Problemen führen, die Neuinstallation des Betriebssystems erforderlich machen können. Sie verwenden den Registrierungs-Editor auf eigene Gefahr.

> [!NOTE]
> Sie benötigen zum Abschneiden oder löschen die Protokolldatei gelegentlich, um zu verhindern, dass es zu groß.

 Das folgende Verfahren beschreibt das Festlegen ein benutzerdefinierten Protokolldateispeicherorts für einen einzelnen Client.

### <a name="to-set-a-custom-log-file-location"></a>Festlegen ein benutzerdefinierten Protokolldateispeicherorts

1. Open **Regedit.exe**.

2. Navigieren Sie zum Knoten `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.

3. Legen Sie den Zeichenfolgenwert `LogFilePath` auf den vollständigen Pfad und Dateiname der Ihre bevorzugte benutzerdefinierten Protokollspeicherort.

     Dieser Speicherort muss sich in einem Verzeichnis auf die der Benutzer Schreibzugriff hat. Beispielsweise unter Windows Vista, erstellen Sie die folgende Ordnerstruktur und die legen `LogFilePath` zu *C:\Users\\\<Benutzername > \Documents\Logs\ClickOnce\installation.log*.

## <a name="see-also"></a>Siehe auch
- [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)
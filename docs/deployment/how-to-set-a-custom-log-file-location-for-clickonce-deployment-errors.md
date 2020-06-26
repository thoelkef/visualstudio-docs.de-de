---
title: Festlegen des benutzerdefinierten Protokolldatei Speicher Orts für ClickOnce-Bereitstellungs Fehler
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 05ffd1cf32f8c7ea93e63232f7026c6c926f9308
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382171"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Vorgehensweise: Festlegen eines benutzerdefinierten Protokolldateispeicherorts für ClickOnce-Bereitstellungsfehler
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]verwaltet Aktivierungs Protokolldateien für alle bereit Stellungen. In diesen Protokollen werden alle Fehler im Zusammenhang mit der Installation und Initialisierung einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung dokumentiert. Standardmäßig wird [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] für jede Bereitstellungs Aktivierung eine Protokolldatei erstellt. Diese Protokolldateien werden im Ordner "temporäre Internet Dateien" gespeichert. Die Protokolldatei für eine Bereitstellung wird dem Benutzer angezeigt, wenn ein Aktivierungs Fehler auftritt, und der Benutzer klickt im resultierenden Fehler Dialogfeld auf **Details** .

 Sie können dieses Verhalten für einen bestimmten Client ändern, indem Sie den Registrierungs-Editor (**regedit.exe**) verwenden, um einen benutzerdefinierten Pfad für die Protokolldatei festzulegen. In diesem Fall [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] protokolliert Aktivierungs Erfolge und-Fehler für alle bereit Stellungen in einer einzelnen Datei.

> [!CAUTION]
> Die fehlerhafte Verwendung des Registrierungs-Editors kann zu schweren Problemen führen, die möglicherweise eine Neuinstallation des Betriebssystems erforderlich machen. Sie verwenden den Registrierungs-Editor auf eigene Gefahr.

> [!NOTE]
> Sie müssen die Protokolldatei gelegentlich abschneiden oder löschen, um zu verhindern, dass Sie zu groß wird.

 Im folgenden Verfahren wird beschrieben, wie ein benutzerdefinierter Speicherort für die Protokolldatei für einen einzelnen Client festgelegt wird.

### <a name="to-set-a-custom-log-file-location"></a>So legen Sie einen benutzerdefinierten Speicherort für Protokolldateien fest

1. Öffnen Sie **Regedit.exe**.

2. Navigieren Sie zum Knoten `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .

3. Legen Sie den Zeichen folgen Wert `LogFilePath` auf den vollständigen Pfad und den Dateinamen Ihres bevorzugten benutzerdefinierten Protokoll Speicher Orts fest.

     Dieser Speicherort muss sich in einem Verzeichnis befinden, auf das der Benutzer Schreibzugriff hat. Erstellen Sie beispielsweise unter Windows Vista die folgende Ordnerstruktur, und legen `LogFilePath` Sie auf *c:\Users \\ \<username> \Documents\Logs\ClickOnce\installation.log*fest.

## <a name="see-also"></a>Siehe auch
- [Problembehandlung bei ClickOnce-Bereitstellungen](../deployment/troubleshooting-clickonce-deployments.md)
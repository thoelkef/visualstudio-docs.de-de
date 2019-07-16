---
title: ClickOnce und Anwendungseinstellungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8e1ffe6d6f32cfad137d5890715a5a0032a29d7
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696685"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce und Anwendungseinstellungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Anwendungseinstellungen für Windows Forms erleichtert das Erstellen, speichern und Verwalten von benutzerdefinierten Anwendungs- und benutzereinstellungen auf dem Client. Das folgende Dokument beschreibt die Funktionsweise der Anwendung-Dateien für konformitätseinstellungen in eine ClickOnce-Anwendung und wie ClickOnce Einstellungen migriert, wenn der Benutzer ein Upgrade auf die nächste Version.  
  
 Die folgenden Informationen gelten nur für der Application Settings-Standardanbieter der <xref:System.Configuration.LocalFileSettingsProvider> Klasse. Wenn Sie einen benutzerdefinierten Anbieter angeben, wird dieses Anbieters bestimmen, wie die Daten gespeichert und wie sie die Einstellungen zwischen den Versionen aktualisiert. Weitere Informationen zum Anbieter von Anwendungseinstellungen, finden Sie unter [Architektur der Anwendungseinstellungen](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="application-settings-files"></a>Anwendungseinstellungen-Dateien  
 Anwendungseinstellungen verwendet zwei Dateien: *app*. exe.config "und" user.config, wobei *app* ist der Name Ihrer Windows Forms-Anwendung. User.config wird auf die Zeit des Clients die erste erstellt die Anwendung benutzerspezifische Einstellungen speichert. *App*. exe.config, im Gegensatz dazu befindet sich vor der Bereitstellung, wenn Sie Standardwerte für Einstellungen definieren. Visual Studio berücksichtigt diese Datei automatisch bei der Verwendung der **veröffentlichen** Befehl. Bei der Erstellung der ClickOnce-Anwendung mit Mage.exe oder MageUI.exe, Sie müssen sicherstellen, diese Datei ist im Lieferumfang Ihrer Anwendung des andere Dateien, wenn Sie sich das Anwendungsmanifest auffüllen.  
  
 In einer Windows Forms-Anwendungen, die nicht mit ClickOnce bereitgestellt, eine Anwendung die *app*. exe.config-Datei wird im Verzeichnis der Anwendung gespeichert, während die Datei user.config des Benutzers gespeichert wird **Dokumente und Einstellungen**  Ordner. In einer ClickOnce-Anwendung *app*. exe.config im Anwendungsverzeichnis innerhalb der ClickOnce-Anwendung-Cache befindet, und user.config befindet sich im ClickOnce-Datenverzeichnis für diese Anwendung.  
  
 Unabhängig davon, wie Sie Ihre Anwendung bereitstellen, stellt sicheren Zugriff auf Anwendungseinstellungen sicher *app*. exe.config und sichere Lese-/Schreibzugriff auf user.config.  
  
 In einer ClickOnce-Anwendung wird die Größe der Konfigurationsdateien ein, die Anwendungseinstellungen von der Größe der ClickOnce-Cache eingeschränkt. Weitere Informationen finden Sie unter [Übersicht über die ClickOnce-Cache](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Upgrades von Serverversionen  
 Genau wie jede Version eine ClickOnce-Anwendung von allen anderen Versionen isoliert ist, werden die Einstellungen für eine ClickOnce-Anwendung aus den Einstellungen für andere Versionen auch isoliert. Wenn der Benutzer auf eine höhere Version der Anwendung aktualisiert wurde, vergleicht Anwendungseinstellungen neueste (höchste nummerierte) Version der Einstellungen für die Einstellungen, die mit der aktualisierten Version und Merges die Einstellungen in einen neuen Satz von Dateien für konformitätseinstellungen angegeben.  
  
 In der folgende Tabelle wird beschrieben, wie Anwendungseinstellungen entscheidet, welche Einstellungen kopiert werden.  
  
|Art der Änderung|Upgradeaktion|  
|--------------------|--------------------|  
|Einstellung hinzugefügt *app*. exe.config|Die neue Einstellung mit der aktuellen Version zusammengeführt wird *app*. exe.config|  
|Einstellung, die daraus *app*. exe.config|Die alte Einstellung wird von der aktuellen Version entfernt *app*. exe.config|  
|Der Standardwert der Einstellung geändert; lokale Einstellung immer noch festgelegt auf die ursprüngliche Standardeinstellung in user.config.|Die Einstellung wird als Wert in der aktuellen Version user.config mit den neuen Standard zusammengeführt.|  
|Der Standardwert der Einstellung geändert; Einstellung auf nicht standardmäßige in user.config festgelegt|Die Einstellung wird in der aktuellen Version user.config mit den nicht standardmäßigen Wert beibehalten zusammengeführt.|  
  
 Wenn Sie Ihre eigenen Anwendungseinstellungen Wrapperklasse erstellt haben und Aktualisierungslogik anpassen möchten, können Sie überschreiben die <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> Methode.  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce und Roaming-Einstellungen  
 ClickOnce funktioniert nicht mit dem roaming-Einstellungen, dadurch kann die Einstellungsdatei, die Sie über Computer hinweg in einem Netzwerk ausführen. Wenn Sie das roaming von Einstellungen benötigen, müssen Sie entweder ein Anwendungsanbieter für die Einstellungen, die Einstellungen über das Netzwerk speichert implementieren oder entwickeln Ihre eigenen benutzerdefinierten Einstellungenklassen zum Speichern von Einstellungen auf einem Remotecomputer befindet. Weitere Informationen im Anbieter von Anwendungseinstellungen finden Sie unter [Architektur der Anwendungseinstellungen](https://msdn.microsoft.com/library/c8eb2ad0-fac6-4ea2-9140-675a4a44d562).  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Übersicht über Anwendungseinstellungen](https://msdn.microsoft.com/library/0dd8bca5-a6bf-4ac4-8eec-5725d08b38dc)   
 [Übersicht über die ClickOnce-Cache](../deployment/clickonce-cache-overview.md)   
 [Zugreifen auf lokale und Remotedaten in einer ClickOnce-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)

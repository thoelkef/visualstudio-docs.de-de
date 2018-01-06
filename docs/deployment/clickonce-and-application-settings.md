---
title: ClickOnce und Anwendungseinstellungen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords: ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 862f51aa7d124c3dbaa6514b666d74c26334e299
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="clickonce-and-application-settings"></a>ClickOnce und Anwendungseinstellungen
Anwendungseinstellungen für Windows Forms erleichtert das Erstellen, speichern und Verwalten von benutzerdefinierten Anwendungen und benutzereinstellungen auf dem Client. Das folgende Dokument beschreibt die Funktionsweise von Einstellungen Anwendungsdateien in einer ClickOnce-Anwendung, und wie ClickOnce Einstellungen migriert, wenn der Benutzer auf die nächste Version aktualisiert.  
  
 Die folgenden Informationen gelten nur für die Anwendung Standardeinstellungsanbieter, die <xref:System.Configuration.LocalFileSettingsProvider> Klasse. Wenn Sie einen benutzerdefinierten Anbieter angeben, wird dieser Anbieter bestimmt, wie die Daten gespeichert und wie sie die Einstellungen zwischen den Versionen aktualisiert. Weitere Informationen zu Application Settings Provider, finden Sie unter [Architektur der Anwendungseinstellungen](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="application-settings-files"></a>Anwendungseinstellungen-Dateien  
 Anwendungseinstellungen nutzt zwei Dateien: *app*. exe.config "und" user.config, wobei *app* ist der Name des Windows Forms-Anwendung. User.config wird auf die Zeit des Clients das erste erstellt die Anwendung benutzerspezifische Einstellungen speichert. *App*. exe.config, im Gegensatz dazu ist vorhanden, vor der Bereitstellung, wenn Sie Standardwerte für Einstellungen definieren. Visual Studio enthält diese Datei automatisch bei der Verwendung der **veröffentlichen** Befehl. Wenn Sie die ClickOnce-Anwendung mit Mage.exe oder MageUI.exe erstellen, müssen Sie sicherstellen, diese Datei ist im Lieferumfang Ihrer Anwendung der andere Dateien aus, wenn Sie das Anwendungsmanifest auffüllen.  
  
 In einer Windows Forms-Anwendungen, die nicht mit ClickOnce bereitgestellt, einer Anwendung des *app*. exe.config-Datei wird im Verzeichnis der Anwendung gespeichert, während die Datei user.config, in der Benutzerliste gespeichert ist **Dokumente und Einstellungen**  Ordner. In einer ClickOnce-Anwendung *app*. exe.config im Anwendungsverzeichnis innerhalb der ClickOnce-Anwendungscache aktiv ist, und user.config befindet sich im ClickOnce-Datenverzeichnis für diese Anwendung.  
  
 Unabhängig davon, wie Sie Ihre Anwendung bereitstellen, wird safe Lesezugriff auf Anwendungseinstellungen sichergestellt *app*. exe.config und sichere Lese-/Schreibzugriff auf user.config.  
  
 In einer ClickOnce-Anwendung wird die Größe der Konfigurationsdateien von Anwendungseinstellungen verwendet, durch die Größe der ClickOnce-Cache eingeschränkt. Weitere Informationen finden Sie unter [ClickOnce-Cache: Übersicht](../deployment/clickonce-cache-overview.md).  
  
## <a name="version-upgrades"></a>Versionsupgrade  
 Ebenso wie jede Version eine ClickOnce-Anwendung aus allen anderen Versionen isoliert ist, sind die Einstellungen für eine ClickOnce-Anwendung aus den Einstellungen für sowie anderen Versionen isoliert. Wenn der Benutzer auf eine höhere Version der Anwendung aktualisiert wurde, vergleicht Anwendungseinstellungen neueste (höchste nummeriert) Version der Einstellungen für den mit der aktualisierten Version und führt die Einstellungen in einem neuen Satz von Einstellungsdateien angegebenen Einstellungen.  
  
 In der folgenden Tabelle wird beschrieben, wie Anwendungseinstellungen entscheidet, welche Einstellungen kopiert.  
  
|Art der Änderung|Upgradeaktion|  
|--------------------|--------------------|  
|Einstellung hinzugefügt *app*. exe.config|Die neue Einstellung wird mit der aktuellen Version zusammengeführt *app*. exe.config|  
|Einstellung daraus *app*. exe.config|Die alte Einstellung wird von der aktuellen Version entfernt *app*. exe.config|  
|Der Standardwert der Einstellung geändert; lokale Einstellung immer noch festgelegt auf ursprüngliche Standardeinstellung in user.config.|Die Einstellung ist in der aktuellen Version user.config durch den neuen Standardwert als Wert zusammengeführt.|  
|Der Standardwert der Einstellung geändert; festgelegt auf eine nicht standardmäßige in user.config|Die Einstellung wird in der aktuellen Version user.config mit den nicht standardmäßigen Wert beibehalten zusammengeführt.|  
  
 Wenn Sie eine eigene Anwendungseinstellungen Wrapperklasse erstellt haben und Aktualisierungslogik anpassen möchten, können Sie überschreiben die <xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A> Methode.  
  
## <a name="clickonce-and-roaming-settings"></a>ClickOnce und Roamingeinstellungen  
 ClickOnce funktioniert nicht mit Roamingeinstellungen, dem die Einstellungsdatei, die Sie über Computer in einem Netzwerk folgen zu können. Wenn Sie die Roamingeinstellungen benötigen, müssen Sie entweder zum Implementieren eines Anwendungseinstellungsanbieter, der über das Netzwerk Einstellungen speichert, oder entwickeln eine eigene benutzerdefinierte Einstellungenklassen zum Speichern von Einstellungen auf einem Remotecomputer befindet. Weitere Informationen in den Einstellungsanbieter finden Sie unter [Architektur der Anwendungseinstellungen](/dotnet/framework/winforms/advanced/application-settings-architecture).  
  
## <a name="see-also"></a>Siehe auch  
 [ClickOnce-Sicherheit und -Bereitstellung](../deployment/clickonce-security-and-deployment.md)   
 [Übersicht über Anwendungseinstellungen](/dotnet/framework/winforms/advanced/application-settings-overview)   
 [Übersicht über die ClickOnce-Cache](../deployment/clickonce-cache-overview.md)   
 [Zugreifen auf lokale und Remotedaten in einer ClickOnce-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
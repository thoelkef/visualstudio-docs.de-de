---
title: ClickOnce und Anwendungseinstellungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, application settings
ms.assetid: 891caba6-faef-4a3c-8f71-60e6fadb60eb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 153df515fc762b7262dce81d8c1d1c4fe617ad61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900610"
---
# <a name="clickonce-and-application-settings"></a>ClickOnce und Anwendungseinstellungen
Anwendungseinstellungen für Windows Forms erleichtert das Erstellen, speichern und Verwalten von benutzerdefinierten Anwendungs- und benutzereinstellungen auf dem Client. Das folgende Dokument beschreibt die Funktionsweise der Anwendung-Dateien für konformitätseinstellungen in eine ClickOnce-Anwendung und wie ClickOnce Einstellungen migriert, wenn der Benutzer ein Upgrade auf die nächste Version.

 Die folgenden Informationen gelten nur für der Application Settings-Standardanbieter der \<XRef: System.Configuration.LocalFileSettingsProvider > Klasse. Wenn Sie einen benutzerdefinierten Anbieter angeben, wird dieses Anbieters bestimmen, wie die Daten gespeichert und wie sie die Einstellungen zwischen den Versionen aktualisiert. Weitere Informationen zum Anbieter von Anwendungseinstellungen, finden Sie unter [Architektur der Anwendungseinstellungen](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="application-settings-files"></a>Application-Dateien für konformitätseinstellungen
 Anwendungseinstellungen verwendet zwei Dateien:  *\<app >. exe.config* und *user.config*, wobei *app* ist der Name Ihrer Windows Forms-Anwendung. *User.config* wird auf dem Client das erste Zeitpunkt benutzerspezifische Einstellungen Ihrer Anwendung speichert erstellt. *\<App >. exe.config*, im Gegensatz dazu befindet sich vor der Bereitstellung, wenn Sie Standardwerte für Einstellungen definieren. Visual Studio berücksichtigt diese Datei automatisch bei der Verwendung der **veröffentlichen** Befehl. Wenn Sie Ihre Anwendung mit ClickOnce erstellen *Mage.exe* oder *MageUI.exe*, achten Sie darauf, diese Datei ist im Lieferumfang Ihrer Anwendung des andere Dateien, wenn Sie sich das Anwendungsmanifest auffüllen.

 In einer Windows Forms-Anwendungen, die nicht mit ClickOnce bereitgestellt, eine Anwendung die  *\<app >. exe.config* Datei befindet sich im Verzeichnis der Anwendung während der *user.config* -Datei wird gespeichert des Benutzers **Benutzerdokumente und-Einstellungen** Ordner. In einer ClickOnce-Anwendung  *\<app >. exe.config* befindet sich im Anwendungsverzeichnis innerhalb der ClickOnce-Anwendung-Cache und *user.config* befindet sich in die ClickOnce-Datenverzeichnis für diese Anwendung.

 Unabhängig davon, wie Sie Ihre Anwendung bereitstellen, stellt sicheren Zugriff auf Anwendungseinstellungen sicher  *\<app >. exe.config*, und sicher Lese-/Schreibzugriff auf *user.config*.

 In einer ClickOnce-Anwendung wird die Größe der Konfigurationsdateien ein, die Anwendungseinstellungen von der Größe der ClickOnce-Cache eingeschränkt. Weitere Informationen finden Sie unter [Übersicht über die ClickOnce-Cache](../deployment/clickonce-cache-overview.md).

## <a name="version-upgrades"></a>Upgrades von Serverversionen
 Genau wie jede Version eine ClickOnce-Anwendung von allen anderen Versionen isoliert ist, werden die Einstellungen für eine ClickOnce-Anwendung aus den Einstellungen für andere Versionen auch isoliert. Wenn der Benutzer auf eine höhere Version der Anwendung aktualisiert wurde, vergleicht Anwendungseinstellungen neueste (höchste nummerierte) Version der Einstellungen für die Einstellungen, die mit der aktualisierten Version und Merges die Einstellungen in einen neuen Satz von Dateien für konformitätseinstellungen angegeben.

 In der folgende Tabelle wird beschrieben, wie Anwendungseinstellungen entscheidet, welche Einstellungen kopiert werden.

|Art der Änderung|Upgradeaktion|
|--------------------|--------------------|
|Einstellung hinzugefügt  *\<app >. exe.config*|Die neue Einstellung mit der aktuellen Version zusammengeführt wird  *\<app >. exe.config*|
|Einstellung, die daraus  *\<app >. exe.config*|Die alte Einstellung wird von der aktuellen Version entfernt  *\<app >. exe.config*|
|Der Standardwert der Einstellung geändert; lokale Einstellung festlegen, die ursprüngliche Standardeinstellung in *user.config*|Die Einstellung mit der aktuellen Version zusammengeführt wird *user.config* durch den neuen Standardwert als Wert|
|Der Standardwert der Einstellung geändert; Festlegen von Set auf nicht standardmäßige in *user.config*|Die Einstellung mit der aktuellen Version zusammengeführt wird *user.config* mit dem nicht standardmäßigen Wert beibehalten|

Wenn Sie Ihre eigenen Anwendungseinstellungen Wrapperklasse erstellt haben und Aktualisierungslogik anpassen möchten, können Sie überschreiben die \<xref:System.Configuration.ApplicationSettingsBase.Upgrade%2A >-Methode.

## <a name="clickonce-and-roaming-settings"></a>ClickOnce und roaming von Einstellungen
 ClickOnce funktioniert nicht mit dem roaming-Einstellungen, dadurch kann die Einstellungsdatei, die Sie über Computer hinweg in einem Netzwerk ausführen. Wenn Sie das roaming von Einstellungen benötigen, müssen Sie entweder ein Anwendungsanbieter für die Einstellungen, die Einstellungen über das Netzwerk speichert implementieren oder entwickeln Ihre eigenen benutzerdefinierten Einstellungenklassen zum Speichern von Einstellungen auf einem Remotecomputer befindet. Weitere Informationen im Anbieter von Anwendungseinstellungen finden Sie unter [Architektur der Anwendungseinstellungen](/dotnet/framework/winforms/advanced/application-settings-architecture).

## <a name="see-also"></a>Siehe auch
- [ClickOnce security and deployment (ClickOnce-Sicherheit und -Bereitstellung)](../deployment/clickonce-security-and-deployment.md)
- [Application settings overview (Übersicht: Anwendungseinstellungen)](/dotnet/framework/winforms/advanced/application-settings-overview)
- [ClickOnce cache overview (Übersicht: ClickOnce-Cache)](../deployment/clickonce-cache-overview.md)
- [Zugreifen auf lokale und Remotedaten in einer ClickOnce-Anwendung](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)